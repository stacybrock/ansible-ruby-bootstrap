# ansible-ruby-bootstrap

Bootstrap a ruby environment on CentOS

The `install` role will build a ruby environment for an unprivileged user using [rbenv](https://github.com/rbenv/rbenv). If the user does not exist, the playbook will create it.

This playbook has been tested with the following:

* Ansible 2.7.x
* CentOS 7

## Configuration

1. Create a file in `inventory/` containing the host(s) to configure. An example is provided in `inventory/example-dist`
1. Create a file in `group_vars/` with the configuration for the environment. An example is provided in `group_vars/example-dist`:

```
---
common:
  create_user: someuser
  user_home: /home/someuser
  ruby_version: 2.6.0
```

* `common.create_user` - name of user account to create
* `common.user_home` - homedir of user account to create
* `common.ruby_version` - version of ruby to install; see [this list](https://github.com/rbenv/ruby-build/tree/master/share/ruby-build) for possibilities

## Running the Playbook

```
$ ansible-playbook -i inventory/dev install.yml
```
