---
title: "graphics problem"
date: 2008-02-24
forum: Absolute Beginner Talk
---

### Post by Dieselguts on 2008-02-24
ok i have 2 graphics problems. my ATI radeon graphics card needs the driver to be enabled but when i press enable on the resticted driver application, it just says
The software source for the package

   xorg-driver-fglrx

 is not enabled. WTF?
i don't know why it does this. the internet is connected. 
2nd problem, i want to install something on the add/remove thing and i try to tick the box to install it. everytime i click this it says The list of applications is not availabe

Click on 'Reload' to load it. To reload the list you need a working Internet connection. 
it does a few loading bars but it does this every time i try to install something and i cannot install anything.
PLEASE HELP

---

### Post by glennric on 2008-02-24
Make sure you have the gutsy-updates restricted repository enabled and install xorg-driver-fglrx in synaptic.

Also, try typing
```
sudo apt-get update
```
in a terminal and tell me what sort of errors you get.

---

### Post by Dieselguts on 2008-02-24
i typed in sudo apt-get update and it came up with

Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/main Translation-en_GB
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/restricted Translation-en_GB
Reading package lists... Done
tom@TomsPC:~$

---

### Post by glennric on 2008-02-24
Is that all it returned?  There should be a lot more than that.  That means you don't have any repositories enabled.  In synaptic go to settings->repositories and add them.

---

### Post by oedha on 2008-02-24
or
go to system - administration - software sources
mark all boxes
close it
reload it
then try to find your driver again

---

### Post by Dieselguts on 2008-02-24
Ok, i enabled the restricted reository and now it comes up with

tom@TomsPC:~$ sudo apt-get update
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/main Translation-en_GB
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/restricted Translation-en_GB
Get: 1 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy Release.gpg [191B] 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/restricted Translation-en_GB
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/restricted Packages
Fetched 1B in 0s (4B/s)
Reading package lists... Done
tom@TomsPC:~$

---

### Post by glennric on 2008-02-24
Now try 
```
sudo apt-get install xorg-driver-fglrx
```
or look in synaptic for the package xorg-driver-fglrx

---

### Post by oedha on 2008-02-24
sudo apt-get install     xorg-driver-fglrx

---

### Post by Dieselguts on 2008-02-24
kk i've installed the driver and it's working fine. could you reply to my new post "more graphics problems" thx

---

