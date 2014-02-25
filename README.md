This repository contain 3 Ansible playbooks that can help you with Symfony2 application
installation and later deploys.

## Provision

This command should be used only once. it's basically a application installation playbook.

```
$ ansible-playbook -i hosts provision.yml
```

## Destroy

Use only when you need to remove application from server. It will remove application sources,
databases and apache configuration from server.

```
$ ansible-playbook -i hosts destroy.yml
```

## Deploy

Use every single time when you need to update your application.
This playbook will not remove current application code from server. It will copy application source to
temp location, do deploy stuff and replace source app with temp.

```
$ ansible-playbook -i hosts deploy.yml
```

#Usage

First of all you should install [Ansible](http://www.ansible.com/home) on your machine,
official [docs](http://docs.ansible.com/intro_installation.html) should help you with that.

Now you need create host file (``cp hosts.dist hosts``). Basically it's enough to put there server
host where your application should be deployed/installed.

Project variables - everything that is related to your project should be configured in 2 files.
``vars.yml`` and ``templates/parameters.yml.js2``. Just copy ``vars.yml.dist`` to ``vars.yml`` and
``templates/parameters.yml.js2.dist`` to ``templates/parameters.yml.js2``.
Every single variable in those files should be self descriptive.

Ok now you should have everything to install project at production server with ``ansible-playbook -i hosts provision.yml``
but before doing it you should check playbook with ``ansible-playbook -i hosts provision.yml --check``

Enjoy!