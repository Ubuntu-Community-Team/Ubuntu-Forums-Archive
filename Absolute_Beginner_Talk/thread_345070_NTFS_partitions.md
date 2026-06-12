---
title: "NTFS partitions"
date: 2007-01-23
forum: Absolute Beginner Talk
---

### Post by guasano on 2007-01-23
I have a computer that is not dual-booting, but does have old ntfs partitions on it.  There are two partitions with data (the NTFS ones) and then the ext3 partition with my Ubuntu data.  I successfully used ntfs-3g to gain read and write acess to the partitions.  Is there some way to remove these partitions one by one (in the hopes that I won't have to back the data up onto disks or something)?  I can move all the ntfs data onto one partition if necessary, thus freeing the other of any data (again, in case I can reformat the partition one at a time).  I'd like to go ahead and turn these two ntfs parts into fat32 or ext3.  I tried gparted, but it doesn't seem to be able to do anything with the ntfs parts.  Thanks for your help.

---

### Post by akniss on 2007-01-23
How are you using gparted? If you are using it from within Ubuntu, I am assuming that the NTFS partitions are already mounted.  gparted cannot perform operations on partitions that are mounted.  Try to issue the command: ```
sudo umount /dev/hdb1
``` and see if you can then perform the needed operations on the partition.  Be sure to back up the data on partition 1 before performing any operations in gparted!!!

---

### Post by guasano on 2007-01-24
Unmounting the partitions did it.  I don't know why I didn't unmount the volumes the first time.  I'll just say I was hungry or tired.  Thanks!

---

