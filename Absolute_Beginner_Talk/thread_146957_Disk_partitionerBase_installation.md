---
title: "Disk partitioner/Base installation"
date: 2006-03-19
forum: Absolute Beginner Talk
---

### Post by Muttonz on 2006-03-19
I'm trying to setup a harddrive to dual boot XP and Ubuntu.  I partitioned it three ways (one for XP OS (ntfs), XP programs (ntfs), and everything Ubuntu (fat32).  I installed XP on the first partition.  Then I went to install Ubuntu.  Now I'm on the disk partitioner part of the Ubuntu installation.  It's very unclear as to what I am *supposed* to do.  How do I specify which partition Ubuntu should install itself in?  What steps do I need to take?

I'm sorry if this is answered in an obvious place, but I looked through the wiki and stuff like the DualBootHowTo's are vague on this matter.

Thanks.

---

### Post by cotcot on 2006-03-19
No worries , any question is worth to be answered.

A good guide for dual boot is : [http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/) This guide is illustrated with screen shots.

I would not install Ubuntu on a FAT32.

---

### Post by steve.horsley on 2006-03-19
I would suggest that you leave some un-partitioned disk space, and tell the installer to use the free space. It should then creeate a system partition for itself, and a swap partition too.

---

