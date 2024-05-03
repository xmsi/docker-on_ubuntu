# Docker Engine, Compose, Portainer on Ubuntu 22
Docker Engine, Compose and Portainer installation on ubuntu 22. Optional: how to change default docker root folder (where images and containers are stored)

## Install docker engine

[tutorial video](https://www.youtube.com/watch?v=M4rWLwzLmwM) tested it works
To install on Ubuntu 22 you should type these commands in your CLI
1. ``$ curl -fsSl https://get.docker.com -o get-docker.sh``
2. ``$ sudo sh get-docker.sh``
3. ``$ sudo groupadd docker``
4. ``$ sudo usermod -aG docker ${USER}`` \
where ${USER} is a variable provided by UNIX-like operating systems that contains the name of the current user, this allows the current user's name to be automatically inserted into the command so that we can add it to the "docker" group.
5. logout from system then log in back

## Install docker compose

[official web-site](https://docs.docker.com/compose/install/standalone/)

1. ``$ curl -SL https://github.com/docker/compose/releases/download/v2.27.0/docker-compose-linux-x86_64 -o /usr/local/bin/docker-compose``
2. ``$ sudo chmod +x /usr/local/bin/docker-compose``

## Optional (Not required) Portainer WEB UI For docker

[official web](https://docs.portainer.io/start/install-ce/server/docker/linux)

`` $ docker run -d -p 8005:8000 -p 9443:9443 --name portainer --restart=always -v /var/run/docker.sock:/var/run/docker.sock -v portainer_data:/data portainer/portainer-ce:latest --http-enabled``

### Also check Dockage as a simple and powerful alternative of Portainer

## Optional (Not required) Change default docker_root folder 

[tutorial web](https://www.baeldung.com/ops/docker-image-change-installation-directory)

1. ``$ mkdir WHEN_YOU_WANT_NEW_ROOT``
2. ``$ sudo nano /etc/docker/daemon.json``

inside

``` 
{ 
   "data-root": "/WHEN_YOU_WANT_NEW_ROOT"
}
```

3. ``$ sudo systemctl restart docker``
4. ``$ docker info -f '{{ .DockerRootDir}}'``
