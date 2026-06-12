---
title: "partitioning for ubuntu installtion"
date: 2006-04-30
forum: Absolute Beginner Talk
---

### Post by superman16885 on 2006-04-30
do u hav any idea abt how to partition disks for linux, does linux recognize fat and ntfs? i did partition a drive in windowm xp using partition magic, but when i am trying to install, it is saying no partitions were found..do i have to format in linux ext2, ext3 or is it ok if i do it in fat, and which mode of installation should i choose when installing, so that i can specify the drive in which i want to install ubuntu 5.10

---

### Post by chriscando on 2006-04-30
As far as I know you cannot install Linux on FAT.  Although fat can be recognized and written to from Linux. NTFS can be read from Linux as well but is not recommend for writting as it may have problems.

Use ext3 or ReiserFS for Linux.

Its still odd that during installation it did not find any partitions.  It should be able to show you your partition table and allow you to make changes and format partitions.

---

### Post by catlett on 2006-04-30
The install can do the partitioning for you. It is a bit difficult to make partitions ahead of time and set mount points.
The install should recognise the partition. You have to choose "manualy edit partition table". It will list all your partitions. Choose the one you made. It will look like /dev/hda2 in linux with vfat for format type. The install is going to change the format to what it wants anyway so having the right format at the start doesn't really matter.
The easiest way to  install is to choose the option "resize existing partition". Ubuntu will shrink the windows partititon, format the space, create a swap and root partition and install the base system. I would recommend going back into Partiton Magic and deleting the new partition, reallocate the free space to the windows partition and then run the install choosing " resize the existing partition".

---

