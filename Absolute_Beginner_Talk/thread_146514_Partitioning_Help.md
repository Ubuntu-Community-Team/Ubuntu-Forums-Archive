---
title: "Partitioning Help"
date: 2006-03-18
forum: Absolute Beginner Talk
---

### Post by BenM on 2006-03-18
Hi, I have been using a dual boot XP/Ubuntu set up for a couple of months now, and would like to devote a larger share of my hard drive to Ubuntu. I have tried to do so through gparted, qtpart, and the Ubuntu LiveCD, but can not make the changes. I can create new file systems from the unallocated space, but can't figure out how to combine it.

Right now I have 4 gigs of unallocated space that I want to switch to my ext3 ubuntu partition, but can not figure out how. Any help would really be appreciated.

---

### Post by mlind on 2006-03-18
If you're trying to modify root partition, it needs to be unmounted first.
Boot using Ubuntu's install cd or LiveCD and don't mount your root partition.

There's been a lot of discussion and tips about doing this procedure succesfully.
You should search some existing threads about the subject.

---

### Post by plors on 2006-03-18
try the latest [gparted livecd]("http://gparted.sourceforge.net/livecd.php") and see if you still have problems.

---

