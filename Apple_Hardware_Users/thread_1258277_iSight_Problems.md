---
title: "iSight Problems"
date: 2009-09-04
forum: Apple Hardware Users
---

### Post by seuzy13 on 2009-09-04
Hi, I'm using Ubuntu 9.04 on a Macbook 2,1.
A little while back, I wiped the OS X partition, because of partition table issues when installing Linux. Anyway, all the iSight installation guides point to using a driver from the Mac partition which I don't have. Surely there's another way to get the camera working?

---

### Post by gotenks05 on 2009-09-04
> **seuzy13 said:**
> Hi, I'm using Ubuntu 9.04 on a Macbook 2,1.
A little while back, I wiped the OS X partition, because of partition table issues when installing Linux. Anyway, all the iSight installation guides point to using a driver from the Mac partition which I don't have. Surely there's another way to get the camera working?


You're out of luck, because you need to go deep into the install disc, which I don't know if it is possible in Ubuntu to do that with a Mac install disc, although you can get the wireless drivers for ndiswrapper from them.  I have a copy of the necessary driver though.

try [this]("http://dl.getdropbox.com/u/332246/AppleUSBVideoSupport")


Note: you'll need to downgrade libv4l-0, due to a flaw because your camera will show green, I started a thread about on this forum, which has no been solved, so search for the solution to the green problem, if the link helps you.

---

