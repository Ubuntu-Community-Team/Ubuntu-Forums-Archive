---
title: "Gcc installed but cannot ./configure ?"
date: 2007-10-05
forum: Absolute Beginner Talk
---

### Post by bambubambu2 on 2007-10-05
already installed gcc with Synaptic from the live cd but:

i tried do compile 2 things and give errors.

ok this is my problem:
i have no internet , none ,only the live cd .

i installed the live cd on my computer and with synapse manager i installed something like g++ and build essential from the live cd + sinoptic manager

the problem : i can't install the multimedia codec becouse seems theat the compiler gcc don't fid something (i don't remember what exactley)

question : what should i do for having the complete gcc compiler ?i found it on the internet (has 45 mb)

ok now what should i do to install the compiler ? must burn the gcc on a cd and use the synoptic on it ?

afterwards must use necesarly the line sudo get-install build essential , or the synoptic does everything?

any ideea to get myself a gcc compiler on my machine?

ok this is what i tried to install :


gst-plugins-ugly-0.10.6 and

gst-plugins-bad 0-10.5


./cofigure

the last line :

Checking for GLID...configure:error:this packege riequire GLib=2.6 to compile


ANY IDEEA ?what should i do ?

DID     sudo apt-get install build-essential     NOTHING
DID   sudo apt-get install libglib2.0-dev        DIDN'T FIND IT.

---

### Post by kevdog on 2007-10-05
Do this

sudo apt-cache search libglib

See what comes up.

---

### Post by Paul820 on 2007-10-05
You really need an internet connection, there is only so much they can fit on a live CD. If that's not possible then you should buy or get someone to download the ubuntu repositories for you. Only the most important things are on the live CD.

---

### Post by [S|G] on 2007-10-05
You can download the libglib2.0-dev package from here:
[http://packages.ubuntu.com/feisty/libdevel/libglib2.0-dev](http://packages.ubuntu.com/feisty/libdevel/libglib2.0-dev)

---

### Post by bambubambu2 on 2007-10-05
After downloading Download libglib2.0-dev,what should i do ?

how can install this package ?

sudo apt-get install  libglib2.0-dev is ok ?

---

### Post by Paul820 on 2007-10-05
No, you will have to compile that aswell, and have you got all the files that libglib2.0-dev depends on? Otherwise when you try to build it, it will ask for them dependencies.

---

### Post by [S|G] on 2007-10-05
You'll donwload a .deb package. You install .deb packages using the dpkg command, like this:

sudo dpkg -i libglib2.0-dev.deb

Note that dpkg doesn't automatically solve dependency problems, so you'll have to manually download and install any required .deb packages to meet the dependecies.

---

