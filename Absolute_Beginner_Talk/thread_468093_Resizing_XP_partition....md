---
title: "Resizing XP partition..."
date: 2007-06-08
forum: Absolute Beginner Talk
---

### Post by TehSnarf on 2007-06-08
Alright, I've already got Ubuntu installed, and I have several other HDD's that I'm using as storage, but my Ubuntu HDD (/dev/hdd) is only 10gig... /dev/hda is a 50gig XP install, /dev/hdb is a 300gig NTFS storage drive. Basically what I'm wanting to do is to either drop the 50gig (/dev/hda) down to 20, and add the extra 30 I come up with to be an extention of /dev/hdd... is there any easy way to do this outside of the installation CD?

---

### Post by ronocdh on 2007-06-08
> **TehSnarf said:**
> Alright, I've already got Ubuntu installed, and I have several other HDD's that I'm using as storage, but my Ubuntu HDD (/dev/hdd) is only 10gig... /dev/hda is a 50gig XP install, /dev/hdb is a 300gig NTFS storage drive. Basically what I'm wanting to do is to either drop the 50gig (/dev/hda) down to 20, and add the extra 30 I come up with to be an extention of /dev/hdd... is there any easy way to do this outside of the installation CD?
[GParted]("http://gparted.sourceforge.net/") might help you here! The Ubuntu partitioner is powered by this, but the dedicated CD for partitioning should offer you greater functionality. Hopefully it's just what you need!

---

