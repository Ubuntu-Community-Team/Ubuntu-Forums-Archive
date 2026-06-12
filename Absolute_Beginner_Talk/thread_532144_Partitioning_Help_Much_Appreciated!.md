---
title: "Partitioning Help Much Appreciated!"
date: 2007-08-22
forum: Absolute Beginner Talk
---

### Post by Noobuntu61 on 2007-08-22
Hey guys when i start to install ubuntu im fine until i get to the partitioning part. It only gives me two choices for partitioning, the whole disk (i want to dual boot with vista so this is not an option) and manual.

I have already partitioned the drive so that i have 20GB set aside in drive F: for ubuntu. problem is when i select the drive and proceed it says that i need to edit in a mount point into a drive. I have no idea what to do.

When i go to edit that partition it presents me with the size which is set, and the an option to set the format as (i have it on FAT32) and then a mount point box.

What do i put in the mount point box and should i set the format as ext3 or another option?

Thanks for any help.

---

### Post by livestockPimp on 2007-08-22
the mount point is what the partition is been used for, if you are installing all of linux on the same partition then you want the "/" mount point. this will also need to be set as bootable.
Ext3 is what you should use for a filesystem.

---

### Post by wpshooter on 2007-08-22
Use manual partitioning option then:

/ = root & like he said root needs to be bootable
/home = home
/swap = swap

make sure you setup a separate home partition, this will save you a lot of grief in the future.

You should use ext3 as file system type.

---

