---
title: "Problem resizing partition"
date: 2007-09-18
forum: Absolute Beginner Talk
---

### Post by TDKTDK on 2007-09-18
I read the similar threads on resizing partitions, but I don't see anything that could solve my problem. I've been trying to figure this out for the last few hours.

During the install of ubuntu on the remaining 320gb of my 400gb HDD (the other 80gb being a freshly installed XP) my partition size couldn't be larger than about 200gb. If I tried to increase it beyond that size some error occured ("end can't be before the start" or something similar). I figured to go ahead with the 200gb partition, since I could resize it later using gparted livecd. 

Now my problem: resizing is impossible. I can't enlarge it, even though a unallocated space is to the right of the ext3 (my boot) partition. I can't even reduce the size! The error message goes as follows:

e2fsck -f -y -v /dev/sda2
Device or resource busy while trying to open...

I tried the umount command, just to make sure it wasn't mounted, but it wasn't. What could this be? Any ideas on how to solve this?

---

### Post by TDKTDK on 2007-09-18
Nobody? Am I asking this in the wrong forum perhaps?

EDIT: Could somebody please point me in the right direction here? Was something not clear enough? I'm quite new to linux, so don't hesitate to ask :s

---

### Post by AngelfireGR on 2007-09-18
> **TDKTDK said:**
> Nobody? Am I asking this in the wrong forum perhaps?

EDIT: Could somebody please point me in the right direction here? Was something not clear enough? I'm quite new to linux, so don't hesitate to ask :s

I had the same problem and I managed to solve it only with the acronis disk director 10 that  running under windows .

After the installation you should click the enlarge partition button then you will check the partition you want to enlarge (ntfs ) and then you will check the partition you want the space to be taken from ( ext3) and then the aply button ..... in 20 minutes you will have your partition resized .

---

### Post by Duck2006 on 2007-09-18
You can try doing it with the gparted live cd

[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

---

### Post by TDKTDK on 2007-09-18
I did it with the livecd, that's what's not working.

Thanks for the reply btw, I'm totally lost here.

---

### Post by TDKTDK on 2007-09-18
> **AngelfireGR said:**
> I had the same problem and I managed to solve it only with the acronis disk director 10 that  running under windows .

After the installation you should click the enlarge partition button then you will check the partition you want to enlarge (ntfs ) and then you will check the partition you want the space to be taken from ( ext3) and then the aply button ..... in 20 minutes you will have your partition resized .

I just want to enlarge my ext3 partition using the already unallocated space and it won't let me.

---

### Post by AngelfireGR on 2007-09-18
> **TDKTDK said:**
> I just want to enlarge my ext3 partition using the already unallocated space and it won't let me.

I tried also with the live cd a lot of times with no success ... try the acronis disk director 10 ... format the analocated space lin ext3 format ... then click the enlarge partiotion .. select your root ext3 partition like the partition to be enlarged ... then check the new ext3 partition that you formated like to take the space from ... put 100 % and click apply... that should work...

---

### Post by TDKTDK on 2007-09-18
Alright, I can't do it right now, but I'll try this tomorrow! Thanks for the help!

---

