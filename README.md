<a href="https://skrepr.com/">
  <p align="center">
    <img width="200" height="100" src="https://skrepr.com/theme/skrepr/img/skrepr.svg?a3d5f79941" alt="skrepr" />
  </p>
</a>
<h1 align="center">Ansible Role Deploy</h1>
<div align="center">
  <a href="https://github.com/skrepr/ansible-role-deploy/releases"><img src="https://img.shields.io/github/release/skrepr/ansible-role-deploy.svg" alt="Releases"/></a><a> </a>
  <a href="https://github.com/skrepr/ansible-role-deploy/blob/main/LICENSE"><img src="https://img.shields.io/github/license/skrepr/ansible-role-deploy" alt="LICENSE"/></a><a> </a>
  <a href="https://github.com/skrepr/ansible-role-deploy/actions/workflows/ci.yml"><img src="https://github.com/skrepr/ansible-role-deploy/actions/workflows/ci.yml/badge.svg" alt="CI"/></a><a> </a>
  <a href="https://github.com/skrepr/ansible-role-deploy/issues"><img src="https://img.shields.io/github/issues/skrepr/ansible-role-deploy.svg" alt="Issues"/></a><a> </a>
  <a href="https://github.com/skrepr/ansible-role-deploy/pulls"><img src="https://img.shields.io/github/issues-pr/skrepr/ansible-role-deploy.svg" alt="PR"/></a><a> </a>
  <a href="https://github.com/skrepr/ansible-role-deploy/commits"><img src="https://img.shields.io/github/commit-activity/m/skrepr/ansible-role-deploy" alt="Commits"/></a><a> </a>
  <a href="https://github.com/skrepr/ansible-role-deploy/stars"><img src="https://img.shields.io/github/stars/skrepr/ansible-role-deploy.svg" alt="Stars"/></a><a> </a>
  <a href="https://github.com/skrepr/ansible-role-deploy/releases"><img src="https://img.shields.io/github/forks/skrepr/ansible-role-deploy.svg" alt="Forks"/></a><a> </a>
</div>

# About

This Ansible role is used for deploying your Docker application on a Debian server

[![Ansible Role](https://img.shields.io/ansible/role/56377)](https://galaxy.ansible.com/skrepr_github/deploy)
[![Ansible Role](https://img.shields.io/ansible/role/d/56377)](https://galaxy.ansible.com/skrepr_github/deploy)
[![Ansible Quality Score](https://img.shields.io/ansible/quality/56377)](https://galaxy.ansible.com/skrepr_github/deploy)

## Requirements

- SSH access to the server
- Git repository with project
- Docker Compose file

## Role Variables

If you want to use a differently named docker-compose file, you can change that. The default is docker-compose.yml

```yaml
docker-compose_name: docker-compose.yml
```

Give the url of the git repo from which needs to be pulled.

```yaml
repository_url: git@github.com:skrepr/ansible-role-deploy.git
```

Give the directory where the application needs te be installed on the server. The default is /home/deploy/project

```yaml
project_directory: /home/deploy/project
```

 Choose the branch you want to use for pulling

```yaml
git_branch: main
```

Choose the port where the docker nginx container will be running. If you're not using nginx or a webserver in the container environment, you can disable it all together.

```yaml
nginx_config: true
nginx_port_container: 8080
```

## Dependencies

None.

## Example Playbook

```yaml
#!/usr/bin/env ansible-playbook


- hosts: production
  become: true
  become_flags: "--preserve-env=SSH_AUTH_SOCK"

  roles:
   - geerlingguy.git
   - geerlingguy.pip
   - geerlingguy.docker
   - geerlingguy.nginx
   - skrepr.deploy
```

## License

MIT / BSD

## Author Information

This role was created in 2021 by [Jeroen van der Meulen](https://github.com/jeroenvandermeulen), commisioned by [Skrepr](https://skrepr.com)
