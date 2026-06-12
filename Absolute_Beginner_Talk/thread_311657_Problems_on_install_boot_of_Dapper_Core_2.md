---
title: "Problems on install boot of Dapper Core 2"
date: 2006-12-03
forum: Absolute Beginner Talk
---

### Post by clownius on 2006-12-03
Ok after much frustration and compiling my own kernel out of desperation on another machine. I can now load 6.06 on my Core 2 sytem.  Unfortunatly i cant get the GUI to work.

Specs are
Core 2 Duo E6400 2.13Ghz
Intel DG965WH motherboard
1Gb (2*512Mb sticks) DDR2 RAM
80Gb SATA HDD
PATA DVD burner that i will soon replace

After it tried to boot GUI i get a flash
tried Xstart and get


```
X Window System Version 7.0.0
Release Date: 21 December 2005
X Protocol Version 11, Revision 0, Release 7.0
Build Operating System:Linux 2.6.12 i686
Current Operating System: Linux (computername) 2.6.19-(name of my compile) #1 SMP Sun Dec 3 20:29:44 EST 2006 i686
Build Date: 16 March 2006
     Before reporting problems, check http://wiki.x.org to make shure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting, (++) from command line, (!!) notice, (II) informational, (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Sun Dec 3 22:54:36 2006
(==) Using config file: "/etc/X11?xorg.conf"
(EE) No devices detected.

Fatal server error:
no screens found
XIO: fatal IO error 104 (Connection reset by peer) on X server ":0.0" after 0 requests (0 know processed) with 0 events remaining.

```
Id really love my GUI back so if anyone can point out where ive messed up or a fix id be extrmely happy.  Ive had this computer for almost a week now and really wanna use it lol

---

### Post by pay on 2006-12-03
Posting the same question twice only wastes the time of people trying to answer the questions. I believe that the problem is you don't have your xorg.conf setup correctly. I don't use Ubuntu (gentoo user) but I think the command is ```
Xorg -config #or
dpkg-reconfigure xserver-xorg
```Also make sure that if you want the opensource drivers that you compilled the kernel with support for them, otherwise install the properitery drivers before you config X

---

### Post by pay on 2006-12-03
Also look at this for problems installing video drivers (fglrx but maybe nvidia aswell). [http://forums.gentoo.org/viewtopic-p-3756560.html#3756560](http://forums.gentoo.org/viewtopic-p-3756560.html#3756560)

---

### Post by lamego on 2006-12-03
Why did you need to compile your own kernel on the first place ?

---

