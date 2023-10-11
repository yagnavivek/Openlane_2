# Openlane_2

Original Site

[openlane_2](https://openlane2.readthedocs.io/en/latest/usage/migration/introduction.html)


# Steps to install Openlane 2

## Installation of required packages

```
sudo apt-get update
sudo apt-get upgrade
sudo apt install -y build-essential python3 python3-venv python3-pip python3-tk make git
```

## Installing Docker

### Uninstall old versions

```
for pkg in docker.io docker-doc docker-compose podman-docker containerd runc; do sudo apt-get remove $pkg; done
```
### Install using APT repository

Before you install Docker Engine for the first time on a new host machine, you need to set up the Docker repository. Afterward, you can install and update Docker from the repository.

### Setup Docker's apt repo

#### Add Docker's official GPG key:
```
sudo apt-get update
sudo apt-get install ca-certificates curl gnupg
sudo install -m 0755 -d /etc/apt/keyrings
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /etc/apt/keyrings/docker.gpg
sudo chmod a+r /etc/apt/keyrings/docker.gpg

echo \
  "deb [arch="$(dpkg --print-architecture)" signed-by=/etc/apt/keyrings/docker.gpg] https://download.docker.com/linux/ubuntu \
  "$(. /etc/os-release && echo "$VERSION_CODENAME")" stable" | \
  sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
sudo apt-get update
```

### Install Latest version of docker

```
sudo apt-get install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin
```

### Verify the installation by running ```hello-world``` image

```
sudo docker run hello-world
```

A successful installation of Docker would have this output:

```
Hello from Docker!
This message shows that your installation appears to be working correctly.

To generate this message, Docker took the following steps:
1. The Docker client contacted the Docker daemon.
2. The Docker daemon pulled the "hello-world" image from the Docker Hub. (amd64)
3. The Docker daemon created a new container from that image which runs the executable that produces the output you are currently reading.
4. The Docker daemon streamed that output to the Docker client, which sent it to your terminal.

To try something more ambitious, you can run an Ubuntu container with:
$ docker run -it ubuntu bash

Share images, automate workflows, and more with a free Docker ID:
https://hub.docker.com/

For more examples and ideas, visit:
https://docs.docker.com/get-started/
```

## Making Docker available without root (Linux only)

```
sudo groupadd docker
sudo usermod -aG docker $USER
```

Reboot your device

```
sudo reboot
```

### Checking the docker installation after reboot

```
docker run hello-world
```

You will get a little happy message of Hello world, once again, but this time without root. If you get any extra lines, try running again. It should give the below output.

```
Hello from Docker!
This message shows that your installation appears to be working correctly.

To generate this message, Docker took the following steps:
1. The Docker client contacted the Docker daemon.
2. The Docker daemon pulled the "hello-world" image from the Docker Hub.
   (amd64)
3. The Docker daemon created a new container from that image which runs the
   executable that produces the output you are currently reading.
4. The Docker daemon streamed that output to the Docker client, which sent it
   to your terminal.

To try something more ambitious, you can run an Ubuntu container with:
$ docker run -it ubuntu bash

Share images, automate workflows, and more with a free Docker ID:
https://hub.docker.com/

For more examples and ideas, visit:
https://docs.docker.com/get-started/
```

### Checking Installation Requirements
In order to check the installation, you can use the following commands:
```
docker --version
python3 --version
python3 -m pip --version
```
Successful outputs will look like this:
```
$ docker --version
Docker version 20.10.16, build aa7e414fdc
$ python3 --version
Python 3.10.5
$ python3 -m pip --version
pip 21.0 from /usr/lib/python3.10/site-packages/pip (python 3.10)
...
Once an environment has been created, you may wish to activate it, e.g. by
sourcing an activate script in its bin directory.
```

## Download and install OpenLane

- Download OpenLane using PIP
```
python3 -m pip install openlane
```
- Run a smoke test for OpenLane:
```
python3 -m openlane --dockerized --smoke-test
```

If the smoke test finishes successfully, congratulations. You’re ready to use OpenLane.

# Explore on your own How to use OpenLane with the official website link given
