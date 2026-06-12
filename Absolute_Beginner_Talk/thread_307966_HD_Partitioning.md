---
title: "HD Partitioning"
date: 2006-11-27
forum: Absolute Beginner Talk
---

### Post by bazzbc on 2006-11-27
Hello,

First post but i've been lingering for a while learning loads so thanks everyone.

I'm currently reinstalling xp and ubuntu from scratch on my laptop and would just like some advice on the best way to partition.

The HD is 80gb and i plan to have the xp install on a 15gb ntfs partiton.  Then a 45gb fat32 partition which i hope i will be able to share between ubuntu and xp. Then ubuntu installed on the remaining space.

Is this the best way to proceed? all feedback gratefully received.

Thanks

---

### Post by newlinux on 2006-11-27
this should be okay, so long as you don't want to store any files larger than 4GB on the FAT32. You could also make the FAT32 partition ext3 (same as your ubuntu will probably be) and use fs-driver in windows. this will allow you access to read and write to your ext3 partitions from windows. There are also expiremental programs (getting more and more stable) that allow you to read and write to NTFS from linux...  I doubt you really need 20GB for ubuntu unless you plan on installing a lot of software. on my dual boot I have 10GB allocated to ubuntu and have so far used only 4 installing everything I want.

---

### Post by cilynx on 2006-11-27
I've done this type of setup quite effectively on many machines.  Just because I hate running out of native space, I would do 20G for each OS, then the rest to fat32 storage.

---

### Post by tonyr1988 on 2006-11-27
> **newlinux said:**
> this should be okay, so long as you don't want to store any files larger than 4GB on the FAT32. You could also make the FAT32 partition ext3 (same as your ubuntu will probably be) and use fs-driver in windows. this will allow you access to read and write to your ext3 partitions from windows. There are also expiremental programs (getting more and more stable) that allow you to read and write to NTFS from linux...  I doubt you really need 20GB for ubuntu unless you plan on installing a lot of software. on my dual boot I have 10GB allocated to ubuntu and have so far used only 4 installing everything I want.
Agree with all of that, but just to clarify: even if you use ext3 or NTFS for the shared partition, I would still make a separate partition for it. Don't "merge" it into your WinXP or Ubuntu partition just because they're the same file system. Right?

---

### Post by cilynx on 2006-11-27
It depends on what you're trying to accomplish.  Partition splitting gets you a little bit of safety as the death of one partition doesn't necessarily mean the death of the others. 

Merging the data into one of your OS partitions is more convenient from the not running out of space perspective, but more annoying in the more folders to click through to get what you want kind of way.

---

