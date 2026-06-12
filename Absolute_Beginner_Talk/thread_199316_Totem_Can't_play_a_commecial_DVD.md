---
title: "Totem Can't play a commecial DVD?"
date: 2006-06-18
forum: Absolute Beginner Talk
---

### Post by Drakkor on 2006-06-18
The source seems encrypted, and can't be read. Are you trying to play an encrypted DVD without libdvdcss?

sudo apt-get install libdvdcss
Password:
Reading package lists... Done
Building dependency tree... Done
Package libdvdcss is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package libdvdcss has no installation candidate   :confused: 

I also checked Add/Remove Programs,and Synaptic, but libdvdcss is nowhere
to be found !  Anyone ?  Thanks

---

### Post by Anduu on 2006-06-18
See here for all your multimedia needs...

[https://wiki.ubuntu.com/RestrictedFormats](https://wiki.ubuntu.com/RestrictedFormats)

---

### Post by Drakkor on 2006-06-18
Well, I found it and extracted the tar.gz to the desktop,then this happened:

drakkor@drakkor:~$ cd /home/drakkor/Desktop/libdvdcss-1.2.9
drakkor@drakkor:~/Desktop/libdvdcss-1.2.9$ ./configure
checking build system type... i686-pc-linux-gnuoldld
checking host system type... i686-pc-linux-gnuoldld
checking target system type... i686-pc-linux-gnuoldld
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... gawk
checking whether make sets $(MAKE)... no
checking for gcc... no
checking for cc... no
checking for cc... no
checking for cl... no
configure: error: no acceptable C compiler found in $PATH
See `config.log' for more details.
drakkor@drakkor:~/Desktop/libdvdcss-1.2.9$ make
bash: make: command not found
drakkor@drakkor:~/Desktop/libdvdcss-1.2.9$
drakkor@drakkor:~/Desktop/libdvdcss-1.2.9$ make
bash: make: command not found
drakkor@drakkor:~/Desktop/libdvdcss-1.2.9$
:confused:

---

### Post by LKRaider on 2006-06-18
No need to compile, just follow the instructions here: [Playing DVD's]("https://wiki.ubuntu.com/RestrictedFormats#head-49d7b89e22f864732e033a68a77cfe144f23af8c")

---

### Post by Drakkor on 2006-06-18
Thanks, LKRaider got it going !  :p

---

