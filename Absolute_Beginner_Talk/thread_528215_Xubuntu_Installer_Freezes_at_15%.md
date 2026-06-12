---
title: "Xubuntu Installer Freezes at 15%"
date: 2007-08-17
forum: Absolute Beginner Talk
---

### Post by scubersteve on 2007-08-17
I'm having a bit of trouble with the live CD installer.
I can go through the entire setup process, but when it gets to actually installing, it freezes at 15%
Nothing moves, not even the mouse.
I can hear the disc spinning, but it stops after about an hour.
I've used multiple CDs, all burned at very low speeds (x2), the ISO follows the md5 checksum, and when the cd scans itself, it finds no errors.

Laptop Specs:
intel celeron 600 mhz
ram: 192 mbs
hd: 10gbs
and a dvd drive with no burning capabilities

---

### Post by oilchangeguy on 2007-08-17
why have you created another thread on the same subject?
[http://ubuntuforums.org/showthread.php?t=528112](http://ubuntuforums.org/showthread.php?t=528112)

---

### Post by ugm6hr on 2007-08-17
Try the AlternateCD.  

192MB is very much on the boundary of LiveCD installation capability, and it may well be that shared graphics memory takes away some of that so it won't work.

If the LiveCD runs, and gets to the desktop, then this is the most likely issue.

I have told people in the past to try creating a swap partition (around 400MB should be fine), then rebooting the LiveCD and try installing again to see if it works.  Worth a try if downloading a new ISO is not feasible.

---

### Post by plucky on 2007-08-17
I've just had the same problem on a Pentium II with 256 MB memory.

I down loaded the ALTERNATE INSTALL iso which uses a text based installer which is very easy to use. I recommend that you try this route.

The live CD install hangs at 15% when it is trying to examine the disk partitions.I even used Gparted CD to create all the partitions I wanted and also the SWAP partition and it still hung at the same place.

Good Luck

---

