---
title: "Partition Problems: Resize or Format?"
date: 2005-11-09
forum: Absolute Beginner Talk
---

### Post by r_choitram on 2005-11-09
Hello,

Just installed ubuntu 5.10 dual-boot w/XP Pro, and now need to either:

1. resize both WIN & Ubuntu hard-disk partitions 
or
2. Format and reinstall both.

Time is of the essence, so 1 seems best for me. So far I have:

1. Installed qtparted v.0.4.4
2. From this, decided what needs to be resized

(dev/hda2: smaller, 
to fit 
dev/hda1: bigger)

Please advise me,
--r_choitram

---

### Post by darrenrxm on 2005-11-09
Careful if you have a ntfs partition on windows. You might want to use partition magic to resize your ntfs partition. Or you could lose all of your windows information. 

If you decide to reinstall windows make sure that you install it with a fat32 file system. Then the linux partition software will play nice with it. 

I keep meaning to change all of my ntfs partitions to fat32 so that I don't have to worry about this. Then I could get rid of partition magic and just use linux partition software.

---

### Post by rajsarkar on 2005-11-09
do take backup of your important data. ;) 

Raj

---

### Post by jrev on 2005-11-09
No need of Partition Magic !

1) you should defragment you windows partition before you start anything else 
2) you can use the Mandriva first install CD (version 9.1 to 10.1) to have an easy partitioning 
3) After the partitions have been changed and the partition table written to disk 
you switch off the computer and start the Install CD of the distribution you want to install 
AFAIK That's the easiest way for beginners
When you come to partitioning, you select manual and keep all partitions as you put them in the first run with mandriva. No more ...

It's a must to arrange and resize you hard disk's partitions  **_before the installation _**

---

### Post by r_choitram on 2007-05-23
Thank you for the advice.

FYI:
- Sharing data between UBUNTU 7.04 and WINXP almost crashed my hard disk.

- So am back with Windows for a while.

Bye for now,
-Raj

---

### Post by r_choitram on 2007-05-23
Thank you for the advice.

FYI:
- Sharing data between UBUNTU 7.04 and WINXP almost crashed my hard disk.

- So am back with Windows for a while.

- Oh well.

Bye for now,
-Raj

---

