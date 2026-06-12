---
title: "Problem with 'make prepare-al' command"
date: 2007-11-29
forum: Absolute Beginner Talk
---

### Post by jck99nz on 2007-11-29
Hi,
I'm following the guide for setting up a PVR in Smith and Still's book 'Practical MythTV.' As part of the process of installing lirc, I had to enter the following commands to install and build kernel headers (p. 53):

$ sudo apt-get install linux-source-VERSION
$ cd /usr/src
$ sudo tar xfj linux-source-VERSION.tar.bz2
$ sudo ln -s /usr/src/linux-source-VERSION /lib/modules/RELEASE/build
$ cd linux-source-VERSION
$ cp /boot/config-RELEASE .config
$ sudo make scripts prepare-all

The first six steps worked okay, but after the last step I got an error message:
make: *** No rule to make target 'prepare-all'. Stop.

The book is based around release 2.6.15-26-386. I'm using Ubuntu 7.10, release 2.6.22-14-generic. Could this account for the error message? Is there a way around it?

I'm very new to linux; I've tried googling 'prepare-all' but found nothing that seemed useful. Thanks for any help you can give. 
Jeff

---

