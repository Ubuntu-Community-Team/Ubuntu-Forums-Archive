---
title: "Just upgraded and"
date: 2006-06-24
forum: Absolute Beginner Talk
---

### Post by theredcross on 2006-06-24
firstly, how do I configure tetex-base? 
```
dan@wickedsweetdude:~$ sudo dpkg --configure -a

```
results in
```
fmtutil failed. Output has been stored in
/tmp/tetex.postinst.XXobDXf3
Please include this file if you report a bug.
dpkg: error processing tetex-base (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of tetex-bin:
 tetex-bin depends on tetex-base (>= 3.0-4); however:
  Package tetex-base is not configured yet.
dpkg: error processing tetex-bin (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of jadetex:
 jadetex depends on tetex-bin (>= 2.0.1-1); however:
  Package tetex-bin is not configured yet.
dpkg: error processing jadetex (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of tetex-extra:
 tetex-extra depends on tetex-base (>= 3.0-11); however:
  Package tetex-base is not configured yet.
 tetex-extra depends on tetex-bin (>= 2.99); however:
  Package tetex-bin is not configured yet.
dpkg: error processing tetex-extra (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 tetex-base
 tetex-bin
 jadetex
 tetex-extra

```
which puts me back to where I started. So is there another way that I am missing?  Failing anything else I'll try a clean whipe and a reinstall of tetex-base/bin/extra/jadetex, but thats a last resort.

---

### Post by croak77 on 2006-06-24
Try purging the packages first to remove any old config files.

sudo apt-get --purge remove package

---

