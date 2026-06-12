---
title: "[SOLVED] About to destroy my usb drives"
date: 2007-12-16
forum: Absolute Beginner Talk
---

### Post by RedNikon on 2007-12-16
All I am trying to do is reformat them to FAT32 and get them to mount, yet this supposed simple task isn't quiting working in my favor. Can anyone give me a simple step by step solution to this problem. I have to different types of drive one 80 gig Lacie, and one 750 gig Seagate. I have tried formating them in windows and I just get a drive full of un-deletable gibberish. So then I try formating in NTFS that works however when I try to mount them in Ubuntu, it's a no go. Any suggestions?

---

### Post by Capricori on 2007-12-16
Have you tried a Ubuntu tool such as GParted to wipe the drives and format as Fat32?

---

### Post by kelvin spratt on 2007-12-16
As far as I know ntfs is enabled by default in Gutsy? Windows does not really like formating large drives in fat 32 it is not supposed to be a problem with SP2 but it does not always want to play. I always use GParted live CD, to format large drives with no problems. Fat 32 is limited to 4gb file sizes, ntfs is not. also I find it best to make partitions on large drives as it is easier to find things also with using windows any virus is hopefully contained in that partition, I keep keep partitions for Linux only and partitions to share with Ms. I don't use ext3 but use JFS partitions as they are very fast and don't have the the 30 boot check which takes a lot of time with large drives. This is not preaching just my personal  experiance.

---

### Post by RedNikon on 2007-12-16
Yay, I got them to work. I downloaded ntfs-config and enabled ntfs support for External Drives. Now every thing works.

---

