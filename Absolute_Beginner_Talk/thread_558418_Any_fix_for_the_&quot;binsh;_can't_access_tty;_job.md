---
title: "Any fix for the &quot;/bin/sh; can't access tty; job control turned off&quot; error yet?"
date: 2007-09-23
forum: Absolute Beginner Talk
---

### Post by TooManyGames on 2007-09-23
I'm using a release version of Feisty and doing a completely fresh install.  There is a XP install on the drive, but I'm booting from the CD and am planning to tell the install to just wipe the HD, but I can't even get that far.

I boot the disc, install options come up, tell it to "Start or Install Kubuntu", it begins the install (displays the Kubuntu logo and the loading bar) then dumps out to the error "bin/sh; can't access tty; job control turned off"

The HD is set as device 0 master, it's plugged into the master IDE connector on the mobo.  I tried plugging it into the secondary IDE connector, I tried setting it to cable select, I tried setting it to device 0 and forcing a device 1 recognition, nothing seems to be working.  It's a relatively old system, but not so old it shouldn't work.  1.3GHz, 512M max memory (maxed out), 80G Samsung IDE drive, dual optical drives, PCI GeForce 4 64M w/ s-vid output, budget ATI PCI video capture card.  I wanted to use it as a test system to try out LinuxMCE, so I figured I'd try a base Kubuntu install first just to make sure the hardware could at least run it.

The real kick in the teeth is I swear up and down I've had Kubuntu on this exact hardware config once before with no problems.

Any help is greatly appreciated.  8*)

---

### Post by Mister.Vash on 2007-09-24
From what I have read on it, the root cause can be a variety of different issues.  One of the common things that I have seen reported and and easy test - instead of choosing to do an install, choose the check media test to make sure that your installation disk is good.

Also, this thread [http://ubuntuforums.org/showthread.php?t=415009](http://ubuntuforums.org/showthread.php?t=415009) contains many. many people talking about how they gathered more information on what occurs prior to the messages showing up and if they found a workaround, what it was.

Regards

---

### Post by alienexplorers on 2007-09-24
Try booting and loading Ubuntu from the Alternate CD.

---

