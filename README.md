# docker-template
template repository for creating a hackweek docker image

This repository builds a [JupyterHub](https://jupyter.org/hub) environment with Repo2Docker [GitHub Actions CI](https://github.com/jupyterhub/repo2docker-action)

[![Action Status](https://github.com/uwhackweek/docker-template/workflows/CI/badge.svg)](https://github.com/uwhackweek/docker-template/actions)
[![Docker Pulls](https://img.shields.io/docker/pulls/uwhackweeks/template)](https://hub.docker.com/r/uwhackweeks/template/tags)
[![BinderHub](https://mybinder.org/badge_logo.svg)](https://mybinder.org/v2/gh/uwhackweek/docker-template/main?urlpath=git-pull?repo=https://github.com/uwhackweek/jupyterbook-template%26amp%3Bbranch=main%26amp%3Burlpath=lab)

https://hub.docker.com/r/uwhackweeks/template/tags

### How to use this template repository

1. Click 'Use this Template' to create a copy of the configuration under your organization
2. Edit README.md to replace all occurances of `uwhackweek/docker-template` to your repo name (for example `uwescience/snowexhack2021`)
3. By default the GitHub actions pushes to a DockerHub organization name matching the github organization name 
    1. ensure you have GitHub Organization secrets corresponding to a DockerHub username and access token


build with GitHub Actions simply by pushing to GitHub

* pull requests trigger image building without pushing to DockerHub
```
git clone https://github.com/uwhackweek/docker-template
cd docker-template
git checkout dev
# make sure dev branch is up-to-date with master
git merge master
# modify environment.yml or other files in binder/
git commit -a -m "modified binder/environment to my liking"
git push
# go to github.com and create a pull request to merge dev changes into master
```

* PRs trigger re-building image
* Commits to master build image and push to DockerHub tagged by github commit sha and 'latest'

### Pull your image to run a local JupyterLab session
```
docker pull uwhackweeks/template:latest
docker run -it --name HACKWEEK -p 8888:8888 uwhackweeks/template:latest jupyter lab --ip 0.0.0.0
docker stop HACKWEEK
docker rm HACKWEEK
```

### Point to a specific tagged image in JupyterHub config
(image: uwhackweeks/template:abhjdh)
https://zero-to-jupyterhub.readthedocs.io/en/latest/reference/reference.html?highlight=profile_list#singleuser-profilelist
