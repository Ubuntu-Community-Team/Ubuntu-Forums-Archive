---
title: "cannot mount ntfs partition"
date: 2005-12-28
forum: Absolute Beginner Talk
---

### Post by wrath on 2005-12-28
hi I am completly new to linux and ubuntu and know nothing about unix operating systems... I need some instructions on how I can mount my windows ntfs partition in ubuntu... I read several posts and tried doing the same thing while changing some things to get it to work with my HD but I just can't access it, could someone please give me a hand?

---

### Post by towsonu2003 on 2005-12-28
Learn where your ntfs partition is with this command: ```
sudo fdisk -l
```
In the following example, /dev/hda2 is an ntfs partition:```
/dev/hda2            2612        6527    31455270    7  HPFS/NTFS

``` -be careful as fdisk is *dangerous*. 

Once you locate your ntfs partition, ```
sudo mkdir /ntfs1
cp /etc/fstab /etc/fstab_backup1
sudo gedit /etc/fstab
```
To the end of that file, copy paste this as one line: 
```
/dev/hda2       /ntfs1       ntfs    ro,nls=utf8,umask=0222        0       0
```
and change /dev/hda2 with your own ntfs partition. Save and close the file. And finish it with ```
sudo mount -a
``` 
Your ntfs partition is under /ntfs but it can only be read-only because linux does not support writing to ntfs (except experimental which means dangerous). But it can write to FAT32, so you can use a flash drive or similar as an intermediary between linux and windows. 

good luck.

If something goes wrong, please post exactly what you did (copy-paste) and the errors, and the output of ```
sudo fdisk -l
cat /etc/fstab
mount | sort
```

---

