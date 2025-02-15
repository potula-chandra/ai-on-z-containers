<!-- This should be the location of the title of the repository, normally the short name -->
# Example on building a development sandbox image 

## Overview

The project contains a container file which demonstrates building a data science developer sandbox for IBM Z (s390x) that can take advantage of the IBM z16 and LinuxONE 4 Integrated Accelerator for AI.

This container file relies on base images from the [IBM Z and LinuxONE Container Image Registry (ICR) ](https://ibm.github.io/ibm-z-oss-hub/main/main.html). Specifically, a TensorFlow base image is utilized. 

Additional packages include:
- ibm-zdnn-plugin (TensorFlow IBM z16 accelerator support)
- xgBoost
- IBM Snap ML
- Scikit-learn
- jupyter


## Usage

This image can be built using the podman or docker build command.  e.g., `docker build -t 's390x-dev' .`

Once this image is built, you can start a container using a command like this:
`docker run -d --rm -p 8571:8888 <image_id> `
Set the port as appropriate

This will start a container which exposing jupyter port 8888 on host system port 8571. 
If you specify -d (as above) you will need to display the jupyter token; this can be found by issuing `docker logs <container_id> `
You can then direct your web browser to `<host_ip_addr>:<exposed_port>/?token=<jupyter_token>`
