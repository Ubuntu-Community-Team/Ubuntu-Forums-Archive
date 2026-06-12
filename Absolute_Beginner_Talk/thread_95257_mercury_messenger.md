---
title: "mercury messenger"
date: 2005-11-26
forum: Absolute Beginner Talk
---

### Post by myd on 2005-11-26
Hi everyone,

I am trying to install mercury messenger on my amd 64, but i am having troubles...

First i do chmod +x 1709_Linux_NoVM.bin and then ./1709_Linux_NoVM.bin, but when installation begins i am having the followwing errors:

Preparing to install...
Extracting the installation resources from the installer archive...
Configuring the installer for this system's environment...
nawk: error while loading shared libraries: libm.so.6: cannot open shared object file: No such file or directory
dirname: error while loading shared libraries: libc.so.6: cannot open shared object file: No such file or directory
/bin/ls: error while loading shared libraries: librt.so.1: cannot open shared object file: No such file or directory
basename: error while loading shared libraries: libc.so.6: cannot open shared object file: No such file or directory
dirname: error while loading shared libraries: libc.so.6: cannot open shared object file: No such file or directory
basename: error while loading shared libraries: libc.so.6: cannot open shared object file: No such file or directory
hostname: error while loading shared libraries: libresolv.so.2: cannot open shared object file: No such file or directory

Launching installer...

grep: error while loading shared libraries: libc.so.6: cannot open shared object file: No such file or directory
/usr/java/jdk1.5.0_05/jre/bin/java: error while loading shared libraries: libpthread.so.0: cannot open shared object file: No such file or directory

Can someone help me? i am lost...

Thank you in advance

---

### Post by ShakingSpirit on 2005-11-26
Looks like you're missing a few libraries :)
All the errors except one need you to 'sudo apt-get install libc6'

The very bottom one however, wants you to install Java. Check through the HOWTO section of the forums (or [http://www.ubuntuguide.org/#jre](http://www.ubuntuguide.org/#jre) **MAY** work) :)

---

### Post by craft47 on 2005-12-06
I just downloaded the file with VM and installed it in my home directory since I'm the only one using.  Works pretty good.  I can send winks although they don't play on my end.

---

