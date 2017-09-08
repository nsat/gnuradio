BUILD INSTRUCTIONS
==================

Included below are instructions for building packages for GNURADIO for the Spire
production stack.

Instructions assume starting from the user's home directory that the user is
in the docker group. Instructions have been tested on hosts that have the 
`testrig` ansible playbook applied.

# Building for Ubuntu 16.04

## Build Instructions
```
git clone --branch spire-3.7.10.1 --recursive git@github.com:nsat/gnuradio.git
docker run -v ~/gnuradio:/gnuradio -it --entrypoint bash ubuntu:16.04
apt-get update > /dev/null
apt-get install -y lsb-core sudo libboost-all-dev > /dev/null
# ** install UHD **
cd /gnuradio
./build.sh
```

## Install UHD
The above instructions reference installing UHD. This is the Spire packaged
UHD found at [nsat/uhd](https://github.com/nsat/uhd). This can be done by
downloading the current released version from the Spire Sandbox or else by
installing a freshly built deb package as instructed in the UHD documentation.

# Building for Ubuntu 12.04:

## Prerequisites
Requires [nsat/air](https://github.com/nsat/air) be cloned locally and the
gsshell docker built from the latest master.


## Build Instructions
```
git clone --branch spire-3.7.10.1 --recursive git@github.com:nsat/gnuradio.git air/gnuradio
./socker gsshell
apt-get install -y --force-yes lsb libpcre3-dev=8.12-4 libpcre3=8.12-4 libglib2.0-dev libpulse-dev > /dev/null
cd gnuradio
./build.sh
```
