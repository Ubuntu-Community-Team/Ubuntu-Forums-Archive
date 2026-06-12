---
title: "[SOLVED] DMA decides to go on holiday - Help"
date: 2007-08-07
forum: Absolute Beginner Talk
---

### Post by forestpixie on 2007-08-07
I seem to have lost DMA on one of my hard drives - it started it's go slow acouple of days ago. Last night I checked hdparm and DMA is reported as off. 

I've tried to turn it on with, but it won't let me - I don't really understand why it would have changed? I have searched here, launchpad and google - but not getting very far.

I've seen that there appears to be a problem with Fesity - but all the threads I've seen are it never working - can't find one where it's changed. 

```

sudo hdparm -d1 /dev/hda1

/dev/hda1:
 setting using_dma to 1 (on)
 HDIO_SET_DMA failed: Invalid argument
 using_dma    =  0 (off)
```
 
Does anyone know if the following upgraded packages would have affected it?

Upgraded the following packages:
dbus (1.0.2-1ubuntu3) to 1.0.2-1ubuntu4
dbus-1-utils (1.0.2-1ubuntu3) to 1.0.2-1ubuntu4
libdbus-1-3 (1.0.2-1ubuntu3) to 1.0.2-1ubuntu4
libqt3-mt (3:3.3.8really3.3.7-0ubuntu5) to 3:3.3.8really3.3.7-0ubuntu5.1
python-launchpad-bugs (0.1.13) to 0.1.13.2
tzdata (2007e-0ubuntu0.7.04) to 2007f-0ubuntu0.7.4


Edit - my fault - had changed case - used a duff cable it appears - watching the monitor on a reboot, a fleeting glimpse of a Primary IDE cable err.. :oops:

---

