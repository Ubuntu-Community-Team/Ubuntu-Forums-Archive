---
title: "xorg won't initialize - gdm fails"
date: 2007-12-01
forum: Absolute Beginner Talk
---

### Post by oeolycus on 2007-12-01
I've posted this in the beginner's forum because all things considered, I'm a newb to Linux/Ubuntu. Never one to act like I don't know what I'm doing, I often find myself in over my head.

I think I may have borked xorg. I installed the Ubuntu minimal cd and went about following [this guide]("http://www.psychocats.net/ubuntu/minimal"). Everything was fine until I tried installing the artwiz fonts with synaptic. On the next reboot, the xserver failed out. I took a look at the log file and it looks like it can't find files or directories at /usr/lib/X11, including fonts, misc, 100dpi, and 75dpi. So I'm pretty sure artwiz blew away whatever fonts the xserver depends upon.

That seems to be the only problem. I tried to aptitude remove xorg and reinstall it, but as its reinstalling the packages, I see the same error flying by: Can't find /usr/lib/X11/fonts/75dpi, and others. I'm unsure how to fix this without reinstalling Ubuntu.

---

### Post by oeolycus on 2007-12-01
subsequent usages of dpkg-reconfigure xserver-xorg (with same settings as worked the first time) have not been successful in reviving it.

---

