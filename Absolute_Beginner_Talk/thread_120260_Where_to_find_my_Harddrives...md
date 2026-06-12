---
title: "Where to find my Harddrives.."
date: 2006-01-21
forum: Absolute Beginner Talk
---

### Post by Drowzee on 2006-01-21
hi, i am having a little trouble locating my harddrive partition as like in windows.. when you would open my computer and see the partitions and choose which one you want to browse.. could someone please tell me what to do?

I made a FAT32 Partition especially for linux that i am searchin for.. (why so i can transfer files between windows and linux... (windows is on the NTFS format, and i was told that there might be problems with linux trying to work with ntfs, and that FAT32 would be better for this..)

Thank You

*~Drowzee~*

---

### Post by cotcot on 2006-01-21
You have to mount partitions you want to see. This can manually (mount) or with /etc/fstab. The unoffial guide gives good instructions : [http://ubuntuguide.org/#windows](http://ubuntuguide.org/#windows) (for Hoary 5.04 but is still OK) or (breezy) [http://easylinux.info/wiki/Ubuntu#Windows](http://easylinux.info/wiki/Ubuntu#Windows)
Does this help you further ?

---

### Post by ysse on 2006-01-21
Hi, 
You may be so lucky that the installation recognized your partition and already has mounted it. Look in System / Administration / Disks. You'll find a tab with Partitions. If you're lucky, your FAT32 partition is already there, and you  can see the Access Path, like /windows/D.

Post again if you don't find the partition there.

---

### Post by Drowzee on 2006-01-21
Hi, well it was detected, the partition i mean, but i could not browse.. but after following the instructions i got it to work, thanx for the help guys

*~Drowzee~*

---

