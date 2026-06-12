---
title: "screen resolution"
date: 2007-07-21
forum: Absolute Beginner Talk
---

### Post by cellardweller on 2007-07-21
background info:
 Fresh install of EMC2-Ubuntu 6.06 desktop-i386
Machine: intel celeron D / 512 mb ram; MB w/via chipset P4M800 pro; onboard video unichrome pro 3d/2d graphics; 64mb shared memory.

problem: screen resolution is 1280x1024 it works fine. I would like to change to 1024x768.
Attempted system/preferences/screen resolution - clicked on drop down for screen resolution: the following options appeared 1280x1024 1024x768 800x600 640x480 1280x768 I clicked on each of the options then clicked on apply and the system crashed on each one except default 1280x1024.

If it were a windows os I would install latest video driver and try again. but. I have no idea what the procedure is for installing a driver in linux or where I might find a compatible driver for linux. I checked with mb manufacturer (PC Chips) and they have only windows drivers.

So, I need some step by step answers or a point in the right direction. Thanks in advance:confused:

---

### Post by koganinja89 on 2007-07-21
I would suggest DLing the newest version of your drivers or ubuntu 7

probly something to do with your driver or the refresh rate of your monitor. try googling:

change refreshrate in linux or ubuntu or what ever

---

### Post by ravenwere on 2007-07-21
I assume you are trialling emc2 for work purposes. If not I would recommend, as above, downloading Ubuntu 7.04 instead.

According to [http://www.linuxcnc.org/](http://www.linuxcnc.org/) the version you have installed is precompiled mainly to allow you to test emc2. The other way of using emc2 is to install the latest version of ubuntu (ie 7.04) and then install emc2 from the package on sourceforge.net as per the website above.

Other than that the issue would seem to lie in the /etc/X11/xorg.conf file. I will hand over any comments on configuring that file to those who know what they're doing.

all the best,
r

---

### Post by alienexplorers on 2007-07-21
Please list your xorg.conf file here.  Use:
> cat /etc/X11/xorg.conf
there may be a way to force 1024x768.

---

