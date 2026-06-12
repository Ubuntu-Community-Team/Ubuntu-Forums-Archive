---
title: "Can't write on FAT32 partition"
date: 2005-12-30
forum: Absolute Beginner Talk
---

### Post by Breaddy3 on 2005-12-30
i've tried reading ubuntuguide.org and followed the directions on how to be able to write to a hard drive with a FAT32 partition, yet, after i went through all the steps, i still couldnt write to the hard drive. Any suggestions?

---

### Post by jimrz on 2005-12-30
you must first unmount the drive you are trying to get write access to then follow the steps in the guide, after you make the changes mount the drive and off you go. Had the same prob 1st time i tried to get at my FAT32 and ntfs partitions

---

### Post by patrick295767 on 2005-12-31
one fat32 line from my /etc/fstab for instance:
```
/dev/hdb5	/mnt/hdb5	vfat	defaults,user,rw,noauto	0	1
```
  
Try first as root to know if it works 
```
mount -t vfat /dev/hdb5 /mnt/hdb5 
```
  
(```
sudo fdisk -l  /dev/hda
```)

---

