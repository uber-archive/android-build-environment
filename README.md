Android Build on Docker Container
===


### Mac OSX

#### Prerequisites

#### Create container with docker-machine  :

    $ docker-machine create -d virtualbox --virtualbox-disk-size "200000"  --virtualbox-memory 4096 --virtualbox-hostonly-cidr "192.168.90.1/24" default

    $ docker-machine upgrade default


#### To build the container image:

    $ eval "$(docker-machine env default)"

    $ docker build -t uber/android-build-environment .

#### Android Build :

    $ cd /path/to/your/android/source/root

    $ docker run -i -v $PWD:/project -t uber/android-build-environment /bin/bash /project/ci/build.sh
