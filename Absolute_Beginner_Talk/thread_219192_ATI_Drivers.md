---
title: "ATI Drivers"
date: 2006-07-19
forum: Absolute Beginner Talk
---

### Post by gaurick on 2006-07-19
Hello everyone. I have a Radeon 9600, and I'm looking to get some drivers set up for it as the graphics on my computer after a fresh install are great, but they seem to be a little bit to be desired. I tried hitting up ATI's website, but from what I read, they only support Redhat and one other flavor of Linux. Can anyone help me out?

Also, the simpler the better. I'm still pretty new to Ubuntu and fairly new to Linux.

---

### Post by Kilz on 2006-07-19
> **gaurick said:**
> Hello everyone. I have a Radeon 9600, and I'm looking to get some drivers set up for it as the graphics on my computer after a fresh install are great, but they seem to be a little bit to be desired. I tried hitting up ATI's website, but from what I read, they only support Redhat and one other flavor of Linux. Can anyone help me out?

Also, the simpler the better. I'm still pretty new to Ubuntu and fairly new to Linux.

You can get the ati-driver-installer from ATI and use this howto.[https://help.ubuntu.com/community/BinaryDriverHowto/ATI#head-26e8b0d4be861a6b7c545dc21c45232f909d8ca2]("https://help.ubuntu.com/community/BinaryDriverHowto/ATI#head-26e8b0d4be861a6b7c545dc21c45232f909d8ca2")
Let me advise against the 8.25.18 drivers presently in the repositories and they are the abaslute worst drivers ever created bt ATI. [Get the 8.26.18 drivers from ATI.]("https://support.ati.com/ics/support/default.asp?deptID=894&task=knowledge&folderID=300")

---

### Post by lzfy on 2006-07-19
The easiest way to install the ATI drivers

> Part 1: ATI Driver

First thing I do from a clean install is:

    * open Synaptic and Settings > Repositories.
    * Find all the unchecked boxes and check them.
    * Once this is done, refresh.
    * Search for fglrx
    * Install xorg-driver-fglrx
    * Exit Synaptic

Open a terminal and:
Code:

sudo aticonfig --initial sudo aticonfig --overlay-type=Xv


now reboot. You should now be running the accelerated ATI driver. You can verify this by opening a terminal and entering:
Code:

fglrxinfo

Look for the following:
Code:

OpenGL vendor string: ATI Technologies Inc. OpenGL renderer string: RADEON 9600 XT Generic OpenGL version string: 2.0.5814 (8.25.18)

then enter:
Code:

glxinfo

and look for:
Code:

OpenGL vendor string: ATI Technologies Inc. OpenGL renderer string: RADEON 9600 XT Generic OpenGL version string: 1.2 (2.0.5814 (8.25.18))

I followed this guide and have now XGL running.

Good luck...

---

### Post by qdvubun on 2006-07-19
> **lzfy said:**
> The easiest way to install the ATI drivers



I followed this guide and have now XGL running.

Good luck...

will this work with ATI 9250 ?

---

### Post by Gonzo_PhD on 2006-07-19
I dualboot Linux and XP. If I install Linux drivers for ubuntu, will it mess up the drivers for XP? I mean, will I still be able to use the XP drivers when I use XP?

---

### Post by Kilz on 2006-07-19
> **Gonzo_PhD said:**
> I dualboot Linux and XP. If I install Linux drivers for ubuntu, will it mess up the drivers for XP? I mean, will I still be able to use the XP drivers when I use XP?

The video drivers for Linux will only effect you Linux install.

---

### Post by lzfy on 2006-07-19
> **qdvubun said:**
> will this work with ATI 9250 ?

I really have no idea, see I'm a newbie too :D

---

### Post by djsroknrol on 2006-07-19
Why not try the OSS "Radeon" driver in Synaptic ?...It's simple, and runs a lot of eye candy...If I remember right gaurick, it should support your card. 

I'm running a 9200SE dual headed, and I run xdesktopwaves, 3ddesk and gcompmgr all with no problems (gcompmgr does run slower than I like it to, but it's a great conversation piece for a possible Ubuntu convert)

---

