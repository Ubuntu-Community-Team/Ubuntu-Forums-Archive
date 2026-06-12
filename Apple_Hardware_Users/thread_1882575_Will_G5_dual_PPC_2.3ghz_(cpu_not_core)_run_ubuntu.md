---
title: "Will G5 dual PPC 2.3ghz (cpu not core) run ubuntu?"
date: 2011-11-17
forum: Apple Hardware Users
---

### Post by donavan on 2011-11-17
I have been reading around and there seems to be a few issues with using linux on the G5 mainly the lack of multiprocessor support out of the box (you can recompile the kernel I guess) and issues with the water cooling system.  Can anyone confirm that Ubuntu will run on my G5 without spending the next year of my life doing so.  I love the G5's hardware but oh how I hate OSX.  Please someone help me get away from Apple's clutches my Intel machine has been stole by the fiance to watch netflix on the TV I need a useable PC ASAP.

EDIT *** Sorry the title is wrong I have the 2.7Ghz CPU's not the 2.3 sorry for the screw up the rest of the information is the same though

---

### Post by foxhound89 on 2011-11-17
Hi,
 I've been looking over the fencepost at the G4 and G5 systems for awhile. This may help:

[https://help.ubuntu.com/11.10/installation-guide/powerpc/hardware-supported.html](https://help.ubuntu.com/11.10/installation-guide/powerpc/hardware-supported.html)

It looks like the G5 is considered Newworld and supported.

---

### Post by donavan on 2011-11-17
Thanks for the reply, I actually already read that but I wasn't sure if there was still an issue with the multiprocessor support or the water cooling system.  Supported and actually working are often a bit different in the Linux world. I guess I will just have to download the latest build and give it a go.

---

### Post by dpny on 2011-11-17
The only issue I found with G5s and Ubuntu is the GPU: the Mac version of the X800 XT isn't supported.

---

### Post by tiresia on 2011-11-18
Multiprocessor is supported. If the right kernel is not installed during the installation - which happened to me when I had a PowerMac 2x2.5 GHz, you can choose and install the right kernel after the installation.

---

### Post by pauljwells on 2011-11-20
I managed to get a kludged 11.10 to install and run on a G5 dual core.

[http://ubuntuforums.org/showpost.php?p=11473448&postcount=31]("http://ubuntuforums.org/showpost.php?p=11473448&postcount=31")

---

