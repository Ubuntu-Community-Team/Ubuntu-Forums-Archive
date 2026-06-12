---
title: "Installing XP for dual boot"
date: 2006-07-26
forum: Absolute Beginner Talk
---

### Post by kookookachooo on 2006-07-26
Hi, I have been a linux man for about 4 months now; totally deleting windows. But now, I realized how much easier it is to play and install games on windows. So is there a way to install Windows XP while keeping all of my linux stuff? I want to install Windows and keep my current linux. I've read that its a hassle and that one should install windows and then linux. But can someone give me a nice and easy 'guide' maybe, or just answer a few questions. 

1.Do you have to partition first? i.e. Gparted,etc.
2.What do you need to partition it as?
3.Could someone give me a 'guide'?

Many thanks in advanced.:D 

Also,off-topic...
I'm trying to make a logical partition in my unallocated space (for music movies). I click new, and I move the size of the box to what I want. But when I try to change the partition to logical it does not let me select it; all I can select is primary. My questions are...

1.Does it matter where the box is located? (left or right)
2.What can I do to make it so I can select logical? 
3.Can this partion be accesed by both windows and linux?

Many thanks appreciated in advanced.:D

---

### Post by kurniawands on 2006-07-26
that day i was installing xp after dapper, and seems that xp won't let me using dual os... so i again re-install my dapper and run dual os till now. 

but something wonder was happen, both of my ntfs is there on my desktop, ready to accessed, while i haven't mount anything that day. 

event on my first installation i wasn't able to mount those disks.. (so i'm still wondering it today)

---

### Post by OpsVentus on 2006-07-26
You can install Windows after Linux but it takes a little more effort.
The steps are:
-Setup all your patitions.
-Install Windows on the correct partition.
-Configure GRUB.

If you tell my how your disk(s)/partition(s) look like I can give you some more conclusive information on how to do it.

If you setup a partition to be fat32 you can acces it on both Windows and Linux read and write. But you are limited in the maximum file-size.
If you set it up as NTFS you can read/write in Windows, read in Linux but writing is not recommended.
If you set it up as ext3 you can read in Windows but writing is a bit unstable, read and write in Linux.

Cheers,
Bart.

---

### Post by kookookachooo on 2006-07-26
This is my Gparted box looks like. I'm looking for a 70Gb storage and 40Gb for windows, in the 110Gb unallocated space.

---

### Post by OpsVentus on 2006-07-26
Well I would move the Linux partitions and put the Windows install on the first partition.
This is a bit dangeraus, and I would recommend backup of your data first.

I would do this:
1 partition: fat32 (windows install/40GB)
2 partition: ext3 (Linux install/20GB)
3 partition: ext3 (Linux home/20GB)
4 partition: swap (Linux swap/1GB)
5 partition: fat32 (data disk/what's left)

To do this follow these steps:
-Boot from GParted Live cd
-move first partition to beginning of the unallocated space
-move the other ext3 partition behind the first in the unallocated
-remove the swap partition
-remove the extended
-create new partition for Windows at the beginning of the disk
-create new swap partition behind the second ext3
-create new fat32 partition at the end of the disk

Then you can install windows, after that you can configure GRUB.

Other option is to create 2 new partitions at the end for Windows and install Windows on that one. After that configure grub.

The logical thing has got something to do with that extend stuff. But I'm sure how that all works.
I only use extended if I want to put more partitions than allowed without it on the disk.

Cheers,
Bart.

---

### Post by OpsVentus on 2006-07-26
About configuring GRUB have a look at:
[http://www.ubuntuforums.org/showthread.php?t=223230](http://www.ubuntuforums.org/showthread.php?t=223230)

Cheers,
Bart.

---

