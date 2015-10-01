* PyCharm Professional Edition 4.5.4
* openjdk
* git
* python 2.7

# PyCharm Professional Edition
This container is only possible because of how easy it is to mount your `X11` socket to a container.  
I decided to try my hand at making a pycharm container for my ubuntu dev box, here goes nothing!  

Since this embeds the Professional Edition, all the licensing restrictions from JetBrains apply.

## xhost permission
docker is going to need permission to mount the `X11` socket. The following command should do the trick:  
``` xhost +local:docker ```

## Get The image  
To get the image, you have two options, you can build it or you can pull it from docker-hub
### Pull
``` docker pull vdemario/pycharm-professional ```
### Build
download the vdemario/pycharm Dockerfile, and navigate to that directory and run the following command:  
``` docker build -t vdemario/pycharm . ```
### Run
If you just want to try out the container do this:

    docker run -it -v /tmp/.X11-unix/:/tmp/.X11-unix/ -e DISPLAY=$DISPLAY --rm vdemario/pycharm  
For a little more persistence try this:

    docker run -it -v /tmp/.X11-unix/:/tmp/.X11-unix/ -v ~/PycharmProjects:/root/PycharmProjects -v ~/.PyCharm40:/root/.PyCharm40 -e DISPLAY=$DISPLAY --rm vdemario/pycharm
#### References
* https://blog.jessfraz.com/post/docker-containers-on-the-desktop/  
* [http://www.developer.com/design/a-guide-to-docker-image-optimization](http://www.developer.com/design/a-guide-to-docker-image-optimization.html)
