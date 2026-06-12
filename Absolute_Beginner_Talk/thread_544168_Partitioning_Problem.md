---
title: "Partitioning Problem?"
date: 2007-09-06
forum: Absolute Beginner Talk
---

### Post by CLUGENHEIM on 2007-09-06
Ok, here is my problem...

I have a computer with Windows XP on it, and I don't want to remove that. I went to partition my HD with GParted, but it doesn't work. It says something about "1088 > 1024 not supported!" or something a long those lines..

I\m going to try partition magic in a minute, and I\m hoping that is going to work. Wish me luck, and give me some advice for if this fails, please. Thanks...

---

### Post by alienexplorers on 2007-09-06
before you partition or resize your partitions run defrag in windows like twice in order to prevent data loss.

---

### Post by CLUGENHEIM on 2007-09-06
Alright, thanks.

Ok, in partition magic, it is saying: "This partition crosses the 1024 cylinder boundaries and may not be bootable."

... it IS bootable, because it is booting Windows, unless it means something else? =/ .This is said before any partitioning is done, FYI. Anyone know how to fix this? -_-

---

### Post by indytim on 2007-09-06
I recommend taking this in careful sequential steps (ie don't do multiple tasks at the same time).  Here's my suggestion (GParted Live or Paritition Magic):

1.  Defrag-Defrag as other poster suggested.
2.  Backup your critical files/folders etc.
3.  Shrink your NTFS partition (don't be too aggressive as you will want to allow room for expansion while getting up to speed in Linux.
4.  If you started with only 1 NTFS partition, then create out of the newly "unallocated s;pace on your hd:
5.  1 ext3 partition (est ~5G).
6. 1 swap partition = 2X RAM
7. 1 ext3 partition (est 3-5G) optional for use as your /home

Note the designation on each of the new partitions you created ie sda3, sda4 etc 
8.  Boot back into your install CD
9.  When you come to the point in the installation where it gives you choices in partitioning options, select the "Manual Partitition" option.
10. Identify your "/" with the partition you created in #5 (note you will also have to set the "format" flag on this partition.
11.  Identify your swap with #6.
12.  Identify your /home with #7 if you so desire.

Proceed 

Good Luck,

IndyTim

---

### Post by hyper_ch on 2007-09-06
for partitioning Vista partitions, use the Vista partitioning tool for it...

---

### Post by alienexplorers on 2007-09-06
If you can afford more space try to make your home partition as big as possible.  It fills up really fast when you start loading lots of programs.  Mine was 10 GB and now I have 4.8GB free.

---

### Post by louieb on 2007-09-06
> **CLUGENHEIM said:**
> ... it is saying: "This partition crosses the 1024 cylinder boundaries and may not be bootable."...

That message is a hold over from the the good old days.  If the PC is less that  10 years old you can pretty much ignore it.  If you wind up getting a GRUB error 18 then you'll have to deal with it by upgrading your BIOS   or changing the way the disk is partitioned.

---

### Post by CLUGENHEIM on 2007-09-06
Thanks for the replies, everyone.

The problem was easily fixed with a BIOS update. =p I've installed Ubuntu successfully. I'm running Ubuntu as I type this, as a matter of fact. =D

---

### Post by dptxp on 2007-09-06
Congratulations.

---

