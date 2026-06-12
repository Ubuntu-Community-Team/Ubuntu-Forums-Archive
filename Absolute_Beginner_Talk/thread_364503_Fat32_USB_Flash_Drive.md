---
title: "Fat32 USB Flash Drive"
date: 2007-02-18
forum: Absolute Beginner Talk
---

### Post by bobbocanfly on 2007-02-18
Hi,
I use Ubuntu 6.10 (sorry dont know its other name) on an old pc and im a bit stuck. I know that the Linux kernel doesnt support drives/partitions with the NTFS/FAT32 filesystems. But i would like to know if there is a workaround?

I have a 160gb external USB HD (NTFS Filesystem) and a 64mb Flash Drive (FAT/32 fs) (yes i know its small but its just for ferrying small files around my laptops). 

I can read from the External HD, but not write and i haven't tried the Flash Drive but i know it wont work fron what i have read.

Is there any way to read and write to NTFS/FAT32 fs's using Ubuntu 6.10, making it still read/writeable on windows?

PS. I thought of reformatting the drives but Windows will only let me do that with NTFS or FAT32

---

### Post by mahiyar on 2007-02-18
Linux has read write abilities with fat32. Without any special commands I'am using my FAT32 USB as a medium to keep files common between windows and linux. I do not have much experience with external hard drives.

---

### Post by mcduck on 2007-02-18
I don't now what you've been reading, but your flash drive should work without any problems, allowing you to both read & write to it.

There are also some Ext2/Ext3 drivers available for Windows, so that might be a solution to the problem with your external NTFS drive.

---

### Post by bobbocanfly on 2007-02-18
> **mahiyar said:**
> Linux has read write abilities with fat32. Without any special commands I'am using my FAT32 USB as a medium to keep files common between windows and linux. I do not have much experience with external hard drives.

Thanks for clearing that up, and replying so quickly. I can use my flash drive to move files between Ubuntu/Windoze :D

Thanks
Bobbocanfly

Edit: mcduck: Will look into those EXT2/3 Drivers, Thanks
Edit2: Tried it on Ubuntu and it didnt work but reformatted it in Windows again and it works perfectly

---

