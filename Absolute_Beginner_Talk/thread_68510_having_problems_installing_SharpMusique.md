---
title: "having problems installing SharpMusique"
date: 2005-09-23
forum: Absolute Beginner Talk
---

### Post by Jim Link on 2005-09-23
Hi, I was trying to install SharpMusique however I can't seem to find its dependencies...

Heres what I got:

```
$ sudo dpkg -i sharpmusique_1-1.0-1_i386.deb
Selecting previously deselected package sharpmusique.
(Reading database ... 101551 files and directories currently installed.)
Unpacking sharpmusique (from sharpmusique_1-1.0-1_i386.deb) ...
dpkg: dependency problems prevent configuration of sharpmusique:
 sharpmusique depends on libc6 (>= 2.3.4-1); however:
  Version of libc6 on system is 2.3.2.ds1-20ubuntu14.
 sharpmusique depends on mono-jit (>= 1.0); however:
  Package mono-jit is not installed.
 sharpmusique depends on libglade2.0-cil (>= 2.3.90); however:
  Package libglade2.0-cil is not installed.
 sharpmusique depends on libglib2.0-cil (>= 2.3.90); however:
  Package libglib2.0-cil is not installed.
 sharpmusique depends on libgtk2.0-cil (>= 2.3.90); however:
  Package libgtk2.0-cil is not installed.
 sharpmusique depends on mono-classlib-1.0 (>= 1.0); however:
  Package mono-classlib-1.0 is not installed.
dpkg: error processing sharpmusique (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 sharpmusique
``` 

I checked in Kynaptic and Synaptic and can't find them...  I even updated all my files and still same problem.

Any and all help would be appreciated.

---

### Post by KingBahamut on 2005-09-23
you need to install the the dependencies listed.

Are you certain you have all the repos enabled, universe and multiverse. 

Check your sources in synaptic.

---

