---
title: "read/write ntfs partitions"
date: 2007-03-25
forum: Absolute Beginner Talk
---

### Post by limelightos on 2007-03-25
how would i be able to write to ntfs on my laptop. it has no internet access

---

### Post by machoo02 on 2007-03-25
Unfortunatly, ntfs write access with the kernel's ntfs driver is only listed as experimental.  There is a great thread in the 'Tips and Tutorials' section that shows you how to use NTFS-3G and Fuse to have transparent r/w with ntfs.  You could download all of the necessary packages on a computer that does have internet access, move them to your laptop and install them using dpkg.

---

### Post by david_kt on 2007-03-25
> **limelightos said:**
> how would i be able to write to ntfs on my laptop. it has no internet access

Download it from here:

[http://packages.ubuntu.com/edgy/otherosfs/ntfs-3g](http://packages.ubuntu.com/edgy/otherosfs/ntfs-3g)

including all the dependencies. And then copy them to your laptop. Install the dependencies first before installing ntfs-3g.

DK

---

### Post by halohunter on 2007-03-25
Be aware that its experamental:

[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_mount_Windows_partitions_.28NTFS.29_on_boot-up.2C_and_allow_users_read_and_write_access](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_mount_Windows_partitions_.28NTFS.29_on_boot-up.2C_and_allow_users_read_and_write_access)

For read only (safe):
[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_mount.2Funmount_Windows_partitions_.28NTFS.29_manually.2C_and_allow_all_users_to_read_only](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_mount.2Funmount_Windows_partitions_.28NTFS.29_manually.2C_and_allow_all_users_to_read_only)

Cheers! from Australia.

---

