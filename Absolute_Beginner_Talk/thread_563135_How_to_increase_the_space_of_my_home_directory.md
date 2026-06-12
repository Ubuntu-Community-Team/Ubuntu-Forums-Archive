---
title: "How to increase the space of my home directory"
date: 2007-09-29
forum: Absolute Beginner Talk
---

### Post by dr_alejandro on 2007-09-29
My HD was divided in C and D. I installed Ubuntu 7.04 via Wubi in the D drive which had about 18 GB free. After installing Ubuntu I still have 8 GB free in D. My problem is that I'm running out of space in my home directory. I believe the default amount of space was 100MB. I would like to increase it to, say a GB. I have check online and all I have seen has to do with partitioning the HD and I'm confuse about that. Actually that is what I would like to avoid.

Is there a way to use my root privileges to increase my user space with a few clicks or with a few commands from the terminal? I already went to System->Administration->Users and Groups but I did not have the option to change my user space.

---

### Post by bodhi.zazen on 2007-09-29
Boot a live CD and use gparted to resize /home

Documentation: [Documentation](http://gparted.sourceforge.net/documentation.php)

Depending on your exact geometry, you may need an updated version of gparted in which case downolad the gparted live Cd :

Download: [Download Gparted](http://easynews.dl.sourceforge.net/sourceforge/gparted/gparted-livecd-0.3.4-8.iso)

---

### Post by dcstar on 2007-09-29
> **dr_alejandro said:**
> My HD was divided in C and D. I installed Ubuntu 7.04 via Wubi in the D drive which had about 18 GB free. After installing Ubuntu I still have 8 GB free in D. My problem is that I'm running out of space in my home directory. I believe the default amount of space was 100MB. I would like to increase it to, say a GB. I have check online and all I have seen has to do with partitioning the HD and I'm confuse about that. Actually that is what I would like to avoid.

Is there a way to use my root privileges to increase my user space with a few clicks or with a few commands from the terminal? I already went to System->Administration->Users and Groups but I did not have the option to change my user space.

If you install the **gparted** package, then you can see you setup more clearly.

If you have a separate /home partition (usually a good idea), then you may be able to extend it using gparted (by using the Ubuntu live CD) it if there is unused disk space following it.

If you don't have a separate /home partition yet, then create one using whatever spare disk space you have, and find the instructions in the forum for setting this up.

---

