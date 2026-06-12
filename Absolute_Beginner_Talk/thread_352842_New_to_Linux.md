---
title: "New to Linux"
date: 2007-02-03
forum: Absolute Beginner Talk
---

### Post by jrbanks on 2007-02-03
New to Linux, but not computers. I have a dell laptop w/ati M-4 video. I have installed Ubuntu 6.0 Alternate. It installed OK but when the reboot happened I lose the video. I know a lot of people are having this problem. I can boot pressing Esc and booting to a command line. I have downloaded the propietary Ati drivers but do not know how to install them from the command line. I am very well versed in Windows and have a moderate understanding of Dos and a little programming. I am not affraid of changing Registry values. I just need a step by step instruction on how to install the new drivers. I would think that for as many people who are having this problem, some one may have created a program to automatically install the fix. I have run the dpkg configuration and tried the ati built in configurer, but does not work.

Any and all help appreciated!

Dell laptop Lattitude 840 processor w/256 cache
128 mb ram
ATI M-4 video
Ubuntu 6.0 alternate Install

---

### Post by taurus on 2007-02-03
From the recovery mode, run

```
dpkg-reconfigure xserver-xorg
```
and pick **vesa** as a Driver for your graphic card.  Then reboot and see if X starts.

```
shutdown -r now
```

---

### Post by kinematic on 2007-02-03
with 128mb of memory you will be better of with xubuntu wich is lighter than ubuntu.

---

