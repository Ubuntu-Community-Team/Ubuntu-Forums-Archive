---
title: "another software install problem"
date: 2006-05-07
forum: Absolute Beginner Talk
---

### Post by david@mc on 2006-05-07
Hi folks
I tried to install some encryption software (Fuse and EncFS) from this month's Linux Format DVD, but when running ./configure all went well until I got the following error.  Any suggesttions for what I need to do? 
Thanks again
David

++++

config.status: creating example/Makefile
config.status: creating include/Makefile
config.status: creating include/config.h
config.status: executing depfiles commands
config.status: executing libtool commands
configure: configuring in kernel
configure: running /bin/sh './configure' --prefix=/usr/local  --cache-file=/dev/null --srcdir=.
checking for a BSD-compatible install... /usr/bin/install -c
checking if FUSE is loaded as a module... no
checking if FUSE module is built into the kernel... no
checking if FUSE module is from official kernel... no
checking kernel source directory... Not found
configure: error:
        *** Please specify the location of the kernel source with
        *** the '--with-kernel=SRCDIR' option
configure: error: /bin/sh './configure' failed for kernel

---

### Post by Sef on 2006-05-07
To compile, you need build-essential.

Open the terminal

sudo apt-get install build-essential

---

### Post by david@mc on 2006-05-07
Hi Sef

I already have build-essential installed, so there must be soemthing else going on? 

Thanks again

David

---

### Post by mostwanted on 2006-05-07
Perhaps you should try downloading the kernel source in Synaptic? If you do a search it should be obvious what package to install.

---

### Post by david@mc on 2006-05-07
Thanks mostwanted.  I've done that now and installed all my updates too. 

Sorry, I was being lazy, and trying to install from the DVD. 

Thanks again for your help. 

David

---

