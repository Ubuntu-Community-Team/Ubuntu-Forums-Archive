---
title: "Getting Started with WiFi"
date: 2007-12-07
forum: Absolute Beginner Talk
---

### Post by lycurgus on 2007-12-07
Hi all.  I recently installed Ubuntu Desktop 7.10 (AMD64 running on a Pentium-D) and am in the process of trying to get my wifi network card to work.  It's an Encore ENLWI-G that supports Windows but not Linux.  I'm trying to get ndiswrapper installed so that I can load the Windows driver but am running into some issues when I try to complie ndiswrapper.  Per the instructions, when I run "make install" it returns erros because it cannot find several C header files (including stdlib.h).  I am somewhat shocked and amused that stdlib.h would not be included with the base distribution.

What package do I need to install in order to complie ndiswrapper under the base installation of Ubuntu?  I couldn't figure it out by just looking at the dependencies.  

Also, once I install ndiswrapper and get the driver loaded, will it automatically work with the network manager that's included with Ubuntu or do I need to take additional steps?

Thanks in advance for any advice!

---

### Post by sailor2001 on 2007-12-07
ndiswrapper-common and ndiswrapper-utils are in your synaptics (system/admin/synaptics)

---

### Post by Lord_Dicranius on 2007-12-07
Yes, it should automatically work with Network Manager once you get it working.  As for ndiswrapper, have you tried installing the package from the repositories?  You can use the Synaptic Package Manager to do this.

**EDIT**
sailor2001 beat me to it :-P

---

