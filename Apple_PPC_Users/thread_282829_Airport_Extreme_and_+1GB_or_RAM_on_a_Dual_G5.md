---
title: "Airport Extreme and +1GB or RAM on a Dual G5"
date: 2006-10-23
forum: Apple PPC Users
---

### Post by plush on 2006-10-23
I'm writing in reference to an old bug which I'm dissapointed hasn't been addressed since the last time I installed Ubuntu on my machine a while back.  Basically if you have more than a gig of RAM and a 64bit system, there is a memory access bug with DMA.  A fix has been released, I think.  If anyone knows anything about this please post!

[https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/38912](https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/38912)

P.S.  It does work in PIO mode but is slow as hell and buggy (obviously due to the nature of PIO) :(

---

### Post by rasec on 2006-10-23
There was a patch for the 2.6.18 kernel, but I don't know if it was merged. Here's a link to the patch if you're interested:

[http://lwn.net/Articles/195774/](http://lwn.net/Articles/195774/)

---

### Post by plush on 2006-10-23
Yikes, I don't think there's a Ubuntu kernel release that recent.  Is it possible to compile that kernel and use it with Ubuntu?  How?  Any ideas of what I can do?  Thanks for the response by the way.:-k

---

### Post by rasec on 2006-10-23
I was going to tell you to wait for eddgy, but it's going to be using a 2.6.17 kernel. 

Here's a custom kernel guide for the g5: 

[http://www.ubuntuforums.org/showpost.php?p=1359285&postcount=5](http://www.ubuntuforums.org/showpost.php?p=1359285&postcount=5)

That guide will give you a working base configuration for your kernel, but I don't think it enables the bcm43xx driver. To enable the bcm43xx driver follow the directions here:

[http://forums.gentoo.org/viewtopic-t-409194.html](http://forums.gentoo.org/viewtopic-t-409194.html)

Good luck!

---

### Post by plush on 2006-10-26
Thanks rasec, but I waited until Edgy came out to see if maybe the fix has been implemented in 2.6.17, and it has!!!  I installed Edgy Eft, on my PowerPC Dual 2.0Ghz 1.5G RAM system (new world mac), copied the firmware I extracted from Tiger for my Broadcom 4306 (the Airport Extreme), modprobe'd bcm43xx and used the network manager to click "Enable" for my wireless card!!  That's IT!!  I'm writing this with a 100%, fully functional, wireless Airport Extreme connection on a 64 bit Powerpc system with more than a gig of RAM for the first time ever!

:mrgreen: :mrgreen: :mrgreen: :mrgreen:

---

### Post by RoadTripDK on 2006-10-31
Can you point me to a HowTo on getting Airport working? I am a newbie with a G5 single (PowerPC 9.1) and Ubuntu Edgy PPC64.

---

