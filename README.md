Ansible LXC Dynamic
=====

Based on [Creating and using LXC containers with Ansible in-memory inventory](http://gauvain.pocentek.net/ansible-to-deploy-lxc-containers.html)


Create LXC containers, and manage them into a single playbook.

### Requirements :

* lxc-python2
* lxc-dev

### SSH config :

```
Host 10.0.3.*
  StrictHostKeyChecking no
```

### Inventory

```
[lxc_hosts]
localhost # LXC server

[lxc_hosts:vars]
ansible_ssh_user=localadmin
ansible_ssh_pass=PASSWORD
ansible_sudo_pass=PASSWORD

[apache]

[apache:vars]
ansible_ssh_pass=ubuntu
ansible_ssh_user=ubuntu

[mysql]

[mysql:vars]
ansible_ssh_pass=ubuntu
ansible_ssh_user=ubuntu

[all:vars]
vars_file=local-vars.yml
```

### Run

`ansible-playbook -i inventory -c local site.yml`
