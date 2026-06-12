---
title: "Installing Ubuntu on an existing partition?"
date: 2007-10-13
forum: Absolute Beginner Talk
---

### Post by Janus%TheDoorman on 2007-10-13
My computer's a Lenovo Z61t ThinkPad, with 3 partitions - 2 NTFS Partitions (C: with my Windows install, and D: where the 'My Documents' and the majority of my data (documents, music, etc.) resides), and an FAT32 IBM recovery partition.

My question is, is it possible to shrink the size of the Windows partition solely on C:, reformat the free space to an ext3 partition for Ubuntu, and leave D: as NTFS to access from either of the dual-booted Ubuntu or Windows XP installs?

I'm not too familiar with partitions in general, and trepidation in this area has been the main reason I haven't made the switch to Ubuntu, but with Windows giving me more issues than I'm willing to deal with anymore, and 7.10 coming up, I wanted to learn my way around 7.04 in the time remaining before uprading.

Thanks in advance.

---

### Post by louieb on 2007-10-13
The short answer is [B]yes.
[/B]Much longer answer is **how**.
[LIST]
[*]Clean up your win install (defrag, get rid of temp files, get rid of stuff you don't use.
[*]Backup
[*]Using the Gparted or System Rescue Live CD:[LIST]
[*]Shrink the NTFS partition
[*]Create an extended partition using all the newly unallocated space.
[*]Create 2 logical partitions inside the extended partition.
[*]one for swap make it 1-2 X size of ram
[*]one for ubuntu rest of space 7 gig minimum[/LIST]
[*]Reboot make sure Windows still works[/LIST]Now your ready to install Linux. Use the manual partitioning option and point the installer to you newly created install and swap partitions. Let ti do its thing and you should be all set.

---

### Post by Janus%TheDoorman on 2007-10-13
Okay, I *think* I understand, but the difference between a logical and extended partition is something I don't understand yet. Which one is which now?

---

### Post by vanadium on 2007-10-13
A drive can only hold at most four primary partitions. You can have more partitions on a drive by using logical partitions instead, which live in an "extended" partition. You have three partitions now, and you need two more to fit Linux. Thus, you will end up with five partitions in total, which is only possible if a few of them reside in an extended partition. According to louieb's suggestion, you will put your two Linux partitions in one extended partition. One partition is for the file system (called root, symbol /) and one is for the swap partition (should be 1 or 2 GB, no more, will hold the swap memory. In Windows, a swap file is used, in Linux these data are written into a separate partition).

---

