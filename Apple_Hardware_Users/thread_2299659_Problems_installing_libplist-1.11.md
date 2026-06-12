---
title: "Problems installing libplist-1.11"
date: 2015-10-20
forum: Apple Hardware Users
---

### Post by Maximilian_Bolch on 2015-10-20
Hi there,


I'm fairly new to Terminal work and I have a problem with the manual installation of Libimobiledevice-1.2.0. I want to connect a new iPod Touch 6G to Ubuntu.

Installation requires the latest version of Libplist-1.11. I downloaded the package, went into the folder and did the following:

sudo ./configure
make

In the end, the following error occured: 
fatal error: opening dependency file .deps/node.Tpo: Permission denied

...
An Ubuntu forum then suggested to try:

make distcheck

This resulted in the following error - probably since the program tried to install Cython:
cannot find input file: `cython/Makefile.in'


Is there any solution to this problem?

Regards
Max

---

### Post by steeldriver on 2015-10-20
Where did you unpack the tarball to (your home dir or a system dir)? You should use a location in your home dir so that you don't need sudo except for the final 'make install'

---

