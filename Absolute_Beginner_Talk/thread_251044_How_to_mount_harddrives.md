---
title: "How to mount harddrives"
date: 2006-09-04
forum: Absolute Beginner Talk
---

### Post by CSIphoto on 2006-09-04
Hello all,

Hope you can assist me.  I have Windows XP pro on sda1 w/ ntfs.  I have another hard drive ATA on hda1 fat32.  Ubuntoo is also on the ATA drive in a seperate partition.  I am unable to access sda1 or hda1.  When I try I get the following:

error: device /dev/hda1 is not removable

error: could not execute pmount


error: device /dev/sda1 is not removable

error: could not execute pmount

How do I mount these drives to be able to access and get read/write permissions?

Bryan

---

### Post by comppsyco on 2006-09-04
Try this:
[https://help.ubuntu.com/community/AutomaticallyMountPartitions](https://help.ubuntu.com/community/AutomaticallyMountPartitions)

---

### Post by szf on 2006-09-04
Take a gander [here]("http://ubuntuguide.org/wiki/Dapper#How_to_mount.2Funmount_Windows_partitions_.28NTFS.29_manually.2C_and_allow_all_users_to_read_only").

---

### Post by CSIphoto on 2006-09-04
Thanks for the assistance.  Both links provided valuable information and now I have access to both drives.

Bryan

---

