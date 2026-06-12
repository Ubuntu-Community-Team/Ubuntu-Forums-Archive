---
title: "Install Windows7"
date: 2011-07-19
forum: Any Other OS
---

### Post by shamz_71 on 2011-07-19
I want to install a new OS , Windows7.
i am running , ubuntu 11.04
 
this is my partition division

 			 			 			 		   		 		 		/dev/sda1       ext4            /       14gb        boot(flag)
/dev/sda2      extended              135 gb
    /dev/sda6  ext4            /home  94gb
      Multimedia#1 ext4                 39 gb
    /dev/sda5     linnux-swap          2 gb


Where will i install  windows 7 ?
Same goes if i want to install bt5?

---

### Post by kazuya on 2011-07-20
This one is tricky. You may have to use some sort of resizing functionality on sda6.
(1) backup /home information somewhere.
(2) Resize sda6 (home partition) to have at least 35 GB for Windows 7 
     (a) sda6 45 GB for /home partition
     (b) sda7 49 GB (rest) for /windows 7 NTFS format
 
You would have to install windows 7 first on that new partition sda7 . - I recommend formating it as NTFS and ensuring that one of your partitions is bootable.
 
Then install Linux distro again while preserving /home/username account.
Hopefully noting in /  or root partition is important as the whole root partition would be deleted.
 
Good luck.

---

### Post by ddastoor on 2011-07-20
> this is my partition division

/dev/sda1 ext4 / 14gb boot(flag)
/dev/sda2 extended 135 gb
/dev/sda6 ext4 /home 94gb
Multimedia#1 ext4 39 gb
/dev/sda5 linnux-swap 2 gb

Hi, from your disk partitioning it seems that sda7 would be a logical partition and i highly doubt you can install windows 7 on a logical partition. AFAIK, windows needs to be installed on a primary partition marked active and bootable, so somehow, you can use a fancy Disk partitioner and then move things around to make another PRIMARY partition /dev/sda2 (extended would then be /dev/sda3  onwards...)

Google "windows 7 logical partition"

- Dinshaw

---

### Post by oldfred on 2011-07-20
ddastoor is correct.

Windows has to boot from a primary NTFS partition with the boot flag (active partition in windows). Win7's standard install uses two partitions, a small 100MB boot/recovery and the main install. One reason for the separate /boot was if you want to encrypt the main install. Otherwise win7 can be installed to one primary NTFS partition.

---

