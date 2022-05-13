# Create a GitHub self-hosted runner

## Create a sudo user, like `github`

```shell
useradd github
passwd github

cp /etc/sudoers /etc/sudoers.orginal

visudo

# add line as below
# %github ALL=(ALL) ALL
```

## Run download scripts

Run the `download` scripts in the runner configuration page, like https://github.com/oam-dev/terraform-controller/settings/actions/runners/new?arch=x64&os=linux

```shell
# Create a folder
$ mkdir actions-runner && cd actions-runner# Download the latest runner package
$ curl -o actions-runner-linux-x64-2.291.1.tar.gz -L https://github.com/actions/runner/releases/download/v2.291.1/actions-runner-linux-x64-2.291.1.tar.gz# Optional: Validate the hash
$ echo "1bde3f2baf514adda5f8cf2ce531edd2f6be52ed84b9b6733bf43006d36dcd4c  actions-runner-linux-x64-2.291.1.tar.gz" | shasum -a 256 -c# Extract the installer
$ tar xzf ./actions-runner-linux-x64-2.291.1.tar.gz
```

## Run config scripts

Run the `download` scripts in the runner configuration page, like https://github.com/oam-dev/terraform-controller/settings/actions/runners/new?arch=x64&os=linux

```shell
[github@xxx actions-runner]$ ./config.sh --url https://github.com/oam-dev/terraform-controller --token AAVM4Q2ZZINJ2O4R3K5YYATCPYBEI

--------------------------------------------------------------------------------
|        ____ _ _   _   _       _          _        _   _                      |
|       / ___(_) |_| | | |_   _| |__      / \   ___| |_(_) ___  _ __  ___      |
|      | |  _| | __| |_| | | | | '_ \    / _ \ / __| __| |/ _ \| '_ \/ __|     |
|      | |_| | | |_|  _  | |_| | |_) |  / ___ \ (__| |_| | (_) | | | \__ \     |
|       \____|_|\__|_| |_|\__,_|_.__/  /_/   \_\___|\__|_|\___/|_| |_|___/     |
|                                                                              |
|                       Self-hosted runner registration                        |
|                                                                              |
--------------------------------------------------------------------------------

# Authentication


√ Connected to GitHub

# Runner Registration

Enter the name of the runner group to add this runner to: [press Enter for Default]

Enter the name of runner: [press Enter for iZj6ccepuz1ebmt0fs7esuZ] bj

This runner will have the following labels: 'self-hosted', 'Linux', 'X64'
Enter any additional labels (ex. label-1,label-2): [press Enter to skip]

√ Runner successfully added
√ Runner connection is good

# Runner settings

Enter name of work folder: [press Enter for _work]

√ Settings Saved.

[github@xxx actions-runner]$ ./run.sh

√ Connected to GitHub

Current runner version: '2.291.1'
2022-05-13 06:21:34Z: Listening for Jobs


```



