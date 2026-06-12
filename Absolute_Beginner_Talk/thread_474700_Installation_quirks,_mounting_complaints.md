---
title: "Installation quirks, mounting complaints"
date: 2007-06-15
forum: Absolute Beginner Talk
---

### Post by showty on 2007-06-15
I'm installing Ubuntu Feisty on my main PC, but its having problems. This PC has a 500GB drive for Windows, and another separate 120GB drive I got for Ubuntu.

During the installation wizard I told it to use the Guided mode and take all of the 120GB drive. It then proceeded to scan for previous OSes, telling me it found none (migration wizard). But after copying all of the files and formatting the drive etc, the installation stops, telling me it can't mount a partition for the migration process.

It does say in the installation summary that it will migrate from the OS on my 500GB drive.. how can I stop this from happening? The installer reckons it can't find an OS.. if Guided mode is the problem, how should I allocate the swap partition size for a 120GB drive (and a system with 2GB RAM)...?

Thanks.

EDIT: Here is a screenshot of the installation summary.
[[IMG]http://img376.imageshack.us/img376/5335/screenshotut6.th.png[/IMG]](http://img376.imageshack.us/my.php?image=screenshotut6.png)

---

### Post by Sparkster185 on 2007-06-15
Try to use the Manual mode (not Guided).  That way you should be able to split your 2nd HD into three partitions (/, /home, swap).  Using this method, I've never had a problem with dual-booting between Windows and Ubuntu.

---

### Post by showty on 2007-06-15
> **Sparkster185 said:**
> Try to use the Manual mode (not Guided).  That way you should be able to split your 2nd HD into three partitions (/, /home, swap).  Using this method, I've never had a problem with dual-booting between Windows and Ubuntu.

Yes... but I don't know how much of the 120GB HDD to allocate to each partition. And I know it will dual-boot fine, thats not the problem.. did you even read my post?

---

### Post by insane_alien on 2007-06-15
allocate about 10gigs to the root partition 1gig for swap(2 if you want to hibernate) and you can shove the rest in a /home partition.

---

### Post by showty on 2007-06-15
Okay I allocated it all (heh, 117GB to /, 2GB swap) but it still tries to grab XP profiles at the end of installation even though it couldn't detect any..

---

