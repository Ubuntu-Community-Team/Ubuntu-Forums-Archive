---
title: "[SOLVED] Installing packages from command line always stops at 99%"
date: 2007-10-21
forum: Absolute Beginner Talk
---

### Post by Blue Sassley on 2007-10-21
I seem to be having a problem when I try and install packages from the command line on my mythtv backend server... I have tried installing mythweb and now apache2 and it seems to always stop at 99%:

> myth@mythtv:~$ sudo apt-get install apache2
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  apache2-mpm-worker apache2-utils apache2.2-common libapr1 libaprutil1
  libpcre3 libpq5
The following NEW packages will be installed:
  apache2 apache2-mpm-worker apache2-utils apache2.2-common libapr1
  libaprutil1 libpcre3 libpq5
0 upgraded, 8 newly installed, 0 to remove and 3 not upgraded.
Need to get 432kB/2313kB of archives.
After unpacking 6443kB of additional disk space will be used.
Do you want to continue [Y/n]? Y
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/main apache2-mpm-worker 2.2.3-3.2ubuntu0.1 [432kB]
99% [Working]    

Can someone help me out and please be very specific as I'm very new to all this,

Thanks for the support ahead of time,
Blue

---

### Post by Blue Sassley on 2007-10-21
I found once I hooked up a monitor to the backend server that one of my CD-ROM drives some how got disconnected from the IDE bus and the system was trying to read the CD to load the rest of the package.

Thanks,
Blue

---

