---
title: "BCM 4331 drivers"
date: 2013-02-13
forum: Any Other OS
---

### Post by Garlandg on 2013-02-13
EDIT:  I figured out how to do it, although I'm not sure it will be stable.  I went to the software sources application and to the additional drivers tab and unselected the proprietary and applied changes, then reselected and applied.  I made sure that the b43 driver wasn't installed, and it works.

The only thing is, this may not work for others because I did a dist-upgrade to raring inside of Mint nadia which is not recommended.  If it does not work, this may be why, but I can't recommend doing this as a fix, as it is most likely unstable.  However, it does make me expect that Mint 15 Olivia will support this chip correctly, if it does not already.

Original Post:

I've been trying to rework my wireless drivers because my school decided to remove the "b" protocol.  I tried installing the bcmwl drivers, and managed to get them to work, but they don't work after a reboot, and I can't replicate the steps that made it work.  

The b43 drivers do not support anything but "b" or "g" with this chip.  Has anyone gotten the wl drivers to work consistently?

Currently running Mint 14 with kernel 3.7.3 installed on a macbook pro retina "base model"

---

### Post by Perfect Storm on 2013-02-13
Moved to Other OS/Distro Talk.

---

### Post by joebow1991 on 2013-02-16
[http://debianandi.blogspot.com/2012/05/linux-mint-12-broadcom-bcm4311-problem.html](http://debianandi.blogspot.com/2012/05/linux-mint-12-broadcom-bcm4311-problem.html)  has everything that you need, just replace vim with nano. You WILL get errors of some things being missing but it SHOULD work...If not than reinstall and try it again.

---

### Post by Garlandg on 2013-02-17
Unfortunately, I think you misunderstood me.  I am looking for a replacement for the b43 drivers for this chip because the b43 drivers only support b/g, and the network I am connecting to supports neither.  I somehow ( have no idea, seems like pure luck) managed to get wl to load and connect successfully with this chip once, but haven't been able to replicate it.  I was mainly wondering if anyone had figured out the trick to it.

I have used the b43 drivers in the past with this chip with a different network and they work.  The problem is the internet here that I have no control over doesn't support the modes that are available with the b43 drivers.

I can get wireless very occasionally with the b43 drivers here, but it lasts for less than 5 seconds so I think it's a false positive. 

Chances are I'll need to wait until someone reverse engineers the chip drivers some more, or use tethering of a phone, but I wanted to see if someone had had any success with wl drivers.  

I appreciate your help though.

Here is the linuxwireless.org info on the drivers for this chip:

PCI-ID:  14e4:4331 
   Supported?:   yes (3.2-rc3+) 
Chip ID:   BCM4331 
   Modes:   b/g 
   PHY version: HT (r1) 
   Alternative drivers:  N/A

I could try ndiswrapper, but I've heard that locks up the computer or crashes it somewhat frequently, but I might give it a shot.

---

