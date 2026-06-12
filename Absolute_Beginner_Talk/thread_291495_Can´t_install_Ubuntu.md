---
title: "Can´t install Ubuntu"
date: 2006-11-02
forum: Absolute Beginner Talk
---

### Post by rionoco on 2006-11-02
hi im new here, i tried to install Ubuntu. i´ve got a live cd Ubuntu 6.06 LTS..i reboot with the disk and i´ve got a failure
my computer has Intel(R) Pentium(R)4 CPU 3.00GHz with 1GB RAM, a ATI Radeon X700 graphics card and a monitor View Sonic VA521...i really need some help in this..i´ve tried everything.i downloaded another Ubuntu by torrent and it was the same story..im dowloading Mandrivia right now but thats not what i want
my failure is:




Failed to start the X server (your graphical interface).
It is likely that it is not set up correctly.

X Windows system version 7.0.0
Release Date 21 December 2005
X Protocol Version 11, Revision 0, Release 7.0

Build Operating System: Linux ubuntu 2.6.15-23-386 #1 PREEMPT Tue
May 23 13:49:40 UTC 2006 i686

Fatal server error:
no screen found
XIO: fatal I0 error 104 (connection reset by peer) on X server ":0.0"
after 0 request (0 known processed with 0 events remaining)
](*,) 

i would really appreciate if someone help me out in this
Thnx

---

### Post by ewl1217 on 2006-11-02
If you go past this error, do you end up at a command line? If you do, try running the following command:
```
sudo dpkg-reconfigure xserver-xorg
```
That will take you through a wizard to configure the X server, which controls the graphical interface. The questions are fairly simple, and many can be left at their default values. You should really be concerned with the resolution and video griver. After you complete that, type:
```
startx
```
If you still get the same error, try it again with different configurations.

---

### Post by rfruth on 2006-11-02
Does
```
 sudo apt-get install xserver-xorg-video-ati
```
help ?

---

### Post by rionoco on 2006-11-02
thank you.. i will try this right away.
if i can´t get to a solution can i write u down a private message so u can give me a few other tips??
:p

---

