---
title: "Cant intsall proftpd"
date: 2008-01-03
forum: Absolute Beginner Talk
---

### Post by joshuanv28 on 2008-01-03
I installed webmin on my box and wanted to install proftpd, i tried to install in webmin but it timed out. when i try to install from bash i get this error!

root@Server-Emachine:/home/josh#  apt-get install proftpd
Reading package lists... Done
Building dependency tree       
Reading state information... Done
proftpd is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
3 not fully installed or removed.
E: Could not get lock /var/cache/apt/archives/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the download directory

Im a newb so im still learning LOL!! But i Love Linux and will never give up, any solutions.

---

### Post by Xavieran on 2008-01-03
Make sure you close all other administrative tools before installing...synaptic,adept ,add-remove and the like...

---

