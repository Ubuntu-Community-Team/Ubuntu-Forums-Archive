---
title: "ndiswrapper"
date: 2007-10-13
forum: Absolute Beginner Talk
---

### Post by slikwill on 2007-10-13
The following is my attempt to install and the results.  This worked two weeks ago.

slikwill@slikwill-laptop:~$ ndiswrapper
The program 'ndiswrapper' is currently not installed.  You can install it by typing:
sudo apt-get install ndiswrapper-common
bash: ndiswrapper: command not found
slikwill@slikwill-laptop:~$ sudo apt-get install ndiswrapper-common
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Suggested packages:
  ndiswrapper-source
The following NEW packages will be installed:
  ndiswrapper-common
0 upgraded, 1 newly installed, 0 to remove and 121 not upgraded.
Need to get 18.0kB of archives.
After unpacking 102kB of additional disk space will be used.
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main ndiswrapper-common 1.38-1ubuntu1 [18.0kB]
Fetched 18.0kB in 0s (21.2kB/s)         
Selecting previously deselected package ndiswrapper-common.
(Reading database ... 88002 files and directories currently installed.)
Unpacking ndiswrapper-common (from .../ndiswrapper-common_1.38-1ubuntu1_all.deb) ...
Setting up ndiswrapper-common (1.38-1ubuntu1) ...
slikwill@slikwill-laptop:~$ cd Workspace1
slikwill@slikwill-laptop:~/Workspace1$ cd DRIVER
slikwill@slikwill-laptop:~/Workspace1/DRIVER$ LS
bash: LS: command not found
slikwill@slikwill-laptop:~/Workspace1/DRIVER$ ls
bcm43xx.cat  bcmwl5.inf  bcmwl5.sys
slikwill@slikwill-laptop:~/Workspace1/DRIVER$ sudo ndiswrapper -i bcmwl5.inf
Error: no versions of ndiswrapper found!
slikwill@slikwill-laptop:~/Workspace1/DRIVER$ ndiswrapper -l
Error: no versions of ndiswrapper found!
slikwill@slikwill-laptop:~/Workspace1/DRIVER$ sudo apt-get install ndiswrapper-common
Reading package lists... Done
Building dependency tree       
Reading state information... Done
ndiswrapper-common is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 121 not upgraded.
slikwill@slikwill-laptop:~/Workspace1/DRIVER$ ndiswrapper -l
Error: no versions of ndiswrapper found!
slikwill@slikwill-laptop:~/Workspace1/DRIVER$

---

### Post by francisco_athens on 2007-10-14
you'll need more than just the ndiswrapper-common files

```
sudo apt-get install ndiswrapper-utils-1.9
```

and follow
[http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_Windows_Wireless_Drivers_.28Ndiswrapper.29](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_Windows_Wireless_Drivers_.28Ndiswrapper.29)

you may also want ndisgtk package for a gui for ndiswrapper...

---

### Post by slikwill on 2007-10-14
Thanks, ndiswrapper installed.
Still can't get my Broadcom 4306 card working though.  Worked before I re-installed 7.04

---

### Post by francisco_athens on 2007-10-14
you may need to re-extract the firmware or blacklist a non-working native driver
there is more complete info here:

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff?highlight=%28bcm43xx%29](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff?highlight=%28bcm43xx%29)

---

### Post by jbaerbock on 2007-10-14
just search synaptic for ndiswrapper and you'll find windows wireless program that is gui :D

Also with a broadcom you have to blacklist the driver Ubuntu tries to use by default.

/etc/modprobe.d/blacklist

then type in: blacklist and then insert driver name (with broadcom usualy bcm43xx)

When you restart the computer will then load the driver you installed instead the Ubuntu default.

---

### Post by slikwill on 2007-10-15
Thanks folks.  Turns out that the only thing I did after my last post was download the updates, ignore it for a day, and turn it off overnight.  Powered up this morning, inserted the card, and VOILA! the lights are on and it connects.  Also one of the threads I followed was the obsolete one  for the bcm43xx-shredder which leaves a diagnostic trail in apt-get.  Tells me itis trapped between install and remove.  Is there a remedy, or will this be benign in the future.

R115321.EXE was the driver package I used after installing the ndiswrapper as specified in the above link.

One of the things I wanted to accomplish was to be able to do a "clean" boot and restore, a concept left over from my mainframe days.  This trial by fire with the wireless makes me feel like this is voodoo technology, so I am going to keep what I have.  Thanks again.

---

### Post by slikwill on 2007-10-15
After another reading of the thread and observing the following:

slikwill@slikwill-laptop:~$ ndiswrapper -l
bcmwl5 : driver installed
        device (14E4:4320) present (alternate driver: bcm43xx)

 I decided to blacklist the bcm43xx.  Tried it but got the following:

slikwill@slikwill-laptop:~/Workspace1$ sudo /etc/modprobe.d/blacklist
sudo: /etc/modprobe.d/blacklist: command not found

---

