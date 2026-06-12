---
title: "triple-booting OSX, Win7, Natty w rEFIt on 13&quot; GT320 MBP. Won't boot. What am I missi"
date: 2011-05-23
forum: Apple Hardware Users
---

### Post by starkruzr on 2011-05-23
So, I'm trying to triple-boot.  Installed OSX, had it use the whole drive.  Repartitioned with Boot Camp, installed Win7.  Tried to boot from USB.  Wouldn't work.  Gave me a text menu where I could choose from a live session, installation or hardware test.  Any of those options resulted in a brief pause, then the screen would blank and a short time later the USB drive would simply turn off and the system became unresponsive.

Tried from CD, similar results.  Then, without me changing anything that I'm aware of, it started jumping straight to trying to start a live session.  The "Ubuntu" boot logo with the bouncing dots underneath it sticks around for about 10 minutes, and then the machine KPs.

What am I doing wrong?

---

### Post by !@!@! on 2011-05-24
I triple booted with minimal headaches. :p

I...
1) installed 7 in Bootcamp, just as you said
2) installed rEFIt
3) partitioned so that free space was just sitting
4) booted into the **DVD** of Ubuntu - seemed to be graphical issues with CD on early 2011 13"
5) installed using the free space

---

### Post by starkruzr on 2011-05-24
> **!@!@! said:**
> I triple booted with minimal headaches. :p

I...
1) installed 7 in Bootcamp, just as you said
2) installed rEFIt
3) partitioned so that free space was just sitting
4) booted into the **DVD** of Ubuntu - seemed to be graphical issues with CD on early 2011 
5) installed using the free space

This turned out to be a problem with the installation media I was using.  Now I am all installed but it seems nothing is supported out of the box -- no Unity (no video drivers, GT320 isn't being detected), spotty trackpad support, etc.

I recall there being a repository one added that was a one-stop shop for Mac support, but I can't find either the repo itself or the (presumably) metapackage to install to fix it.

---

