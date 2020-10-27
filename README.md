# Ansible Role Homebrew

## Install XCode cli tools

```shell script
xcode-select --install
```

## Install Homebrew

```
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install.sh)"
```

## Install Ansible

```shell script
brew install ansible
```

### Create roles directory

```shell script
mkdir -p ~/Projects/ansible/roles
cd ~/Projects/ansible
```

```
cat > ansible.cfg <<EOF
[defaults]
inventory = localhost
EOF
```

```
cat > localhost <<EOF
[localhost]
127.0.0.1  ansible_connection=local
EOF
```
### Clone the repository

```shell script
git clone https://github.com/nocbot-project/nocbot-role-homebrew roles/nocbot-role-homebrew
```

### Create Playbook

```shell script
cp roles/nocbot-role-homebrew/homebrew-playbook-example.yml homebrew-playbook.yml
```

Or if you are ok with the example playbook, create a symlink to it (you don't want to do this as I make changes to this file but do not take pull requests for changes):

```shell script
ln -s $(pwd)/roles/nocbot-role-homebrew/homebrew-playbook-example.yml $(pwd)/homebrew-playbook.yml
```

### Run ansible-playbook

```shell script
ansible-playbook --ask-become-pass homebrew-playbook.yml
```
