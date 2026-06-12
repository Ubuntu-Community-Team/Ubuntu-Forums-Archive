---
title: "how do i install gxmame"
date: 2007-05-15
forum: Absolute Beginner Talk
---

### Post by cosmoshell on 2007-05-15
how do i install gxmame on amd64

---

### Post by renzokuken on 2007-05-15
first you need the xmame packages which are already in synaptic

System -> Administration -> Synaptic Package Manager

search for xmame and install it. this is the back end. gxmame is simply a frontend for this.

get the gxmame source by clicking on this link [http://prdownloads.sourceforge.net/gxmame/gxmame-0.34b.tar.gz?download](http://prdownloads.sourceforge.net/gxmame/gxmame-0.34b.tar.gz?download)

now save it to your home folder, right click on it and select "extract here"

now open the terminal and do the following

```
sudo apt-get install build-essential
```
(needed in order to compile things from source)

anter the folder you just extracted with

```
cd gxmame*
```

then to install it run the following 3 commands in order

```
./configure
make
sudo make install
```

it is worth noting that gxmame is very outdated and doesnt work that well with all games. may be worth searching for a newer more up to date frontend

---

### Post by cosmoshell on 2007-05-15
i get this 
root@devil-laptop:/home/devil/Desktop/5# sudo apt-get install build-essential
Reading package lists... Done
Building dependency tree       
Reading state information... Done
build-essential is already the newest version.
The following packages were automatically installed and are no longer required:
  libfreebob0 abiword-common libjack0.100.0-0 libwavpack1 libgstreamer0.8-0
  libcdaudio1 libsoundtouch1c2 libimlib2 libmms0
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
root@devil-laptop:/home/devil/Desktop/5# cd gxmame*
-bash: cd: gxmame*: No such file or directory
root@devil-laptop:/home/devil/Desktop/5# cd /home/devil/gxmame
-bash: cd: /home/devil/gxmame: No such file or directory
root@devil-laptop:/home/devil/Desktop/5# cd /home/devil/gxmame-0.34b
root@devil-laptop:/home/devil/gxmame-0.34b# ./configure
creating cache ./config.cache
checking for non-GNU ld... /usr/X11R6/bin/ld
checking if the linker (/usr/X11R6/bin/ld) is GNU ld... yes
checking for a BSD compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking whether make sets ${MAKE}... yes
checking for working aclocal... missing
checking for working autoconf... missing
checking for working automake... missing
checking for working autoheader... missing
checking for working makeinfo... missing
checking for strerror in -lcposix... no
checking for gcc... gcc
checking whether the C compiler (gcc  ) works... yes
checking whether the C compiler (gcc  ) is a cross-compiler... no
checking whether we are using GNU C... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking how to run the C preprocessor... gcc -E
checking for ANSI C header files... yes
checking for strchr... yes
checking for inflate in -lz... no
configure: error: Cannot find zlib
root@devil-laptop:/home/devil/gxmame-0.34b# make
make: *** No targets specified and no makefile found.  Stop.
root@devil-laptop:/home/devil/gxmame-0.34b# apt-get install zlib
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package zlib


also can you recommend me a better program and tell me how to install it?

---

### Post by prophetargy on 2007-12-11
```
sudo apt-get install kxmame
```

---

