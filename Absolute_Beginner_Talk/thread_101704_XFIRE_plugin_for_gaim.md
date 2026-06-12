---
title: "XFIRE plugin for gaim"
date: 2005-12-10
forum: Absolute Beginner Talk
---

### Post by Griff on 2005-12-10
So I have the tar.gz for it and extracted it, but can't seem to get any further.  I installed the gaim-dev package but that doesn't seem to help me with the problem I'm having.  I tried configuring and got the following message:

stephen@ubuntu:~$ cd ~/downloads
stephen@ubuntu:~/downloads$ ls
Automatix                       gaim-xfire-0.5.8
automatix-ubuntu_v3.4.5.tar.gz  gaim-xfire-0.5.8.tar.gz
stephen@ubuntu:~/downloads$ cd gaim-xfire-0.5.8
stephen@ubuntu:~/downloads/gaim-xfire-0.5.8$ ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking whether make sets $(MAKE)... no
checking for working aclocal-1.4... missing
checking for working autoconf... missing
checking for working automake-1.4... missing
checking for working autoheader... missing
checking for working makeinfo... missing
checking for sed... /bin/sed
checking for gcc... no
checking for cc... no
checking for cc... no
checking for cl... no
configure: error: no acceptable C compiler found in $PATH
See `config.log' for more details.
stephen@ubuntu:~/downloads/gaim-xfire-0.5.8$

?

---

### Post by nikopol on 2005-12-10
Have you installed build-essential?

if not do```
sudo apt-get install build-essential
```
and see how far you get after installing it.

---

### Post by Griff on 2005-12-10
Awesome.  Was able to configure and compile it.  I did the typical ./configure; make; make install, but I get an error for the make install part:

stephen@ubuntu:~/downloads/gaim-xfire-0.5.8$ sudo make install
Making install in src
make[1]: Entering directory `/home/stephen/downloads/gaim-xfire-0.5.8/src'
make[2]: Entering directory `/home/stephen/downloads/gaim-xfire-0.5.8/src'
make[2]: Nothing to be done for `install-exec-am'.
/bin/sh ../mkinstalldirs /usr/local/lib/gaim
/bin/sh ../libtool --silent  --mode=install /usr/bin/install -c libxfire.la /usr/local/lib/gaim/libxfire.la
make[2]: Leaving directory `/home/stephen/downloads/gaim-xfire-0.5.8/src'
make[1]: Leaving directory `/home/stephen/downloads/gaim-xfire-0.5.8/src'
Making install in pixmaps
make[1]: Entering directory `/home/stephen/downloads/gaim-xfire-0.5.8/pixmaps'
make[2]: Entering directory `/home/stephen/downloads/gaim-xfire-0.5.8/pixmaps'
make[2]: Nothing to be done for `install-exec-am'.
/bin/sh ../mkinstalldirs /usr/local/share/pixmaps/gaim/status/default
 /usr/bin/install -c -m 644 ./xfire.png /usr/local/share/pixmaps/gaim/status/default/xfire.png
make[2]: Leaving directory `/home/stephen/downloads/gaim-xfire-0.5.8/pixmaps'
make[1]: Leaving directory `/home/stephen/downloads/gaim-xfire-0.5.8/pixmaps'
make[1]: Entering directory `/home/stephen/downloads/gaim-xfire-0.5.8'
make[2]: Entering directory `/home/stephen/downloads/gaim-xfire-0.5.8'
make[2]: Nothing to be done for `install-exec-am'.
make[2]: Nothing to be done for `install-data-am'.
make[2]: Leaving directory `/home/stephen/downloads/gaim-xfire-0.5.8'
make[1]: Leaving directory `/home/stephen/downloads/gaim-xfire-0.5.8'

edit: I did this again using sudo to gain permission, but still no luck.

PS: What's the forum syntax for putting code in? ;)

---

