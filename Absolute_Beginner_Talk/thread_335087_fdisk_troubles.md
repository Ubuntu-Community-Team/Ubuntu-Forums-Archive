---
title: "fdisk troubles"
date: 2007-01-09
forum: Absolute Beginner Talk
---

### Post by loincloth170 on 2007-01-09
I'm trying to make a new partition to install Slackware on my computer, which already has three partitions (Windows, Ubuntu, and swap). I'm going to use fdisk, but everytime I do, I type "n", but it gives me an error saying there are no more available sectors left. I thought that you could have four, and I only have three, so what's the problem? Thanks!

---

### Post by loincloth170 on 2007-01-10
When I run fdisk -l this is what it displays:

Device         Boot     Start       End           Blocks          Id            System
/dev/sda1    *               1         5099      40957686      7           HPFS/NTFS
/dev/sda2                 5100      9561       35841015    83             Linux
/dev/sda3                  9562     9726       1325362+    82       Linux swap/Solaris

---

### Post by yager on 2007-01-10
You may have better luck with Gpartd.  You can find a LiveCD that will boot to a stripped down desktop with Gpartd and a few other rescue tools.  You can then manipulate your partitions graphically.

Check the link.

[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

---

### Post by loincloth170 on 2007-01-10
Alright, the problem seems to be that I have no more free space on my hard drive. I am going to get a partition utility and cut down my windows space by about 15 GB, and use that for Slackware.

---

