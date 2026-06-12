---
title: "[SOLVED] If I partition my Ubuntu HD, will I lose my files?"
date: 2008-02-03
forum: Absolute Beginner Talk
---

### Post by DayOldPorridge on 2008-02-03
I'm sure I probably won't, but I'm just making sure.  I'm planning to install Hardy Heron Alpha4 on the new partition.

---

### Post by jan quark on 2008-02-03
if you you just shrink the partition using for instance
[URL="http://gparted-livecd.tuxfamily.org/"]
gparted live cd[/URL]

then no

but it is better to ask more than to cry after lost data
so ask

---

### Post by bumanie on 2008-02-03
With the gparted live cd, I have moved partitions, copied partitions, deleted partitions and resized partitions. I have never had anything go wrong, but it can go wrong. Therefore, backup anyhting that is important before you do the partition changes - just in case.

---

### Post by DayOldPorridge on 2008-02-03
Well, I don't have the live CD, but I do have gparted.

Anyway, I just tried unmounting sda1, but got an error:

> The partition could not be unmounted from the following mountpoints:

/

Most likely other partitions are also mounted on these mountpoints. You are advised to unmount them manually

And then gparted just closes.

Is there something else I'm supposed to do?

---

### Post by forestpixie on 2008-02-03
shouldn't need to unmount anything - are you saying that when you boot with gparted it's mounting partitions?

Edit - reread the post :) - what are you using to get gparted - if it's you're install then you can't do it there - need to use either the ubuntu livecd, the gparted livecd or systemrescue which has it on or the list goes on - but basically you're not going to be able to do any partition work with mounted drives

and as an aside make sure you've got backups

---

### Post by ugm6hr on 2008-02-03
> **DayOldPorridge said:**
> Well, I don't have the live CD, but I do have gparted.

Anyway, I just tried unmounting sda1, but got an error:


I would recommend you use Gparted on a LiveCD.  You cannot unmount your / partition from an installed Linux distro.

Also - back up your data before editing partitions - accidents do happen.

---

### Post by Vadi on 2008-02-03
If you're unsure, post a screenshot (press the PrtSc, or Print Screen key) of your installer setup and we'll tell you what'll happen.

---

### Post by DayOldPorridge on 2008-02-03
No, I was just following what it said in the help files about partitioning the hard drive.

Hmm, and booting with gparted?  All I'm doing is running the application straight from Ubuntu.

But apparently I can't make a new partition without unmounting a partition and then resizing it.


EDIT: Oh, guess I better get the Ubuntu LiveCD, then.  Thanks for clearing up the confusion, though.

---

