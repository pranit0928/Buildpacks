# Cloud Native Buildpacks

## What is CNBs?

The CNB project was initiated by Pivotal and Heroku in January 2018 and joined the Cloud Native Computing Foundation (CNCF) as an Apache-2.0 licensed project in October 2018.

Cloud Native Buildpacks (CNBs) transform your application source code into container images that can run on any cloud.

With buildpacks, organizations can concentrate the knowledge of container build best practices within a specialized team, instead of having application developers across the organization individually maintain their own Dockerfiles.

This makes it easier to know what is inside application images, enforce security and compliance requirements, and perform upgrades with minimal effort and intervention.

## Why CNBs?

. Control - Balanced control between App Devs and Operators.

. Compliance - Ensure apps meet security and compliance requirements.

. Maintainability - Perform upgrades with minimal effort and intervention.

## Features of CNBs:

. It auto-detects your code's programming language and its version.

. Advanced Caching.

. Images can be built directly from application source without additional instructions.

. Supports more than one programming language family.

. Image contains only what is necessary.

. Leverage production-ready buildpacks maintained by the community.

. Deploy NodeJS application using Cloud Native Builpacks

## Pre-requisites:

. AWS account.

. An Ubuntu EC2 machine t2.micro (t2.micro is ok, if you are using simple application)

. Docker installed

## Steps:

1. Update your machine

```
  sudo apt update
```

2. Install docker

```
  sudo apt install docker.io -y
```

3. Provide permission to ubuntu user to docker group

```
  sudo usermod -aG docker $USER && newgrp docker
```

4. Install pack utility to build image

```
  sudo add-apt-repository ppa:cncf-buildpacks/pack-cli
  sudo apt-get update
  sudo apt-get install pack-cli
```

5. Clone your code

```
  git clone https://github.com/pranit0928/Buildpacks.git
```

6. Go inside the directory

```
  cd node-todo-cicd
```

7. Remove Dockerfile and docker-compose file to make sure we are not using it for building the image.

```
  rm -rv Dockerfile
  rm -rv docker-compose.yaml
```

8. Run the following command to get the pack builder

```
  pack build suggest
```

9. Copy the google builder and paste in the below command

```
  pack build --builder=<your-builder-from-above-command> node-app
```

------------- [Note] > This build will take some time be patient.

10. After build, check images

```
 docker images
```

11. Run the image as a container

```
 docker run -itd --name nodeapp -p 8080:8080 node-app
```

Note-: This application runs on port 8080, that's why we mentioned 8080 in the above command

12. Open port 8080 from the security groups and access your application

```
 http://<public-ip>:8080
```

## Congratulations!!! you have deployed and application using Cloud Native Buildpacks.
