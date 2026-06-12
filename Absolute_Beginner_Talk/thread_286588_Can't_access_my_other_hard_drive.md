---
title: "Can't access my other hard drive"
date: 2006-10-27
forum: Absolute Beginner Talk
---

### Post by jefuchs on 2006-10-27
My PC has two hard drives.  I installed Ubuntu on the smaller one (20GB), thinking I could use the larger one for extra file storage.

The other hard drive is formatted for Win XP (NTFS), but I believe Linux can still read and write it (I may be wrong).  I don't want to re-format it just yet, as it still has WinXP installed on it.

I'm a beginner, but I believe the other hard drive should be located at dev/hdb1.  When I try to access that location via the File Browser or the command line, it doesn't let me even browse the contents, much less move files there.

How do I use this other drive without being Root?

---

### Post by tonyr1988 on 2006-10-27
Try:

> sudo mount -t ntfs /dev/db1 /second_hdd

The files and folders from your second hard drive should be under /second_hdd. However: this only does it temporarily. When you reboot your computer, it will be reset to the default. However, there's an easy way to make it permanent. I just always try the temporary solution first to make sure it'll work.

NOTE: the /second_hdd can be whatever folder you want it to be - just make sure something else isn't there first!

---

### Post by jorn on 2006-10-28
You can read windows ntfs files, but writing is still experimental.
To find the correct partition of xp paste or write into terminal:
> sudo fdisk -l
To mount them read this section:
[http://ubuntuguide.org/wiki/Ubuntu_dapper#How_to_mount_Windows_partitions_.28NTFS.29_on_boot-up.2C_and_allow_all_users_to_read_only](http://ubuntuguide.org/wiki/Ubuntu_dapper#How_to_mount_Windows_partitions_.28NTFS.29_on_boot-up.2C_and_allow_all_users_to_read_only)
If you are on edgy there is a link here to also write on ntfs:
[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_mount_Windows_partitions_.28NTFS.29_on_boot-up.2C_and_allow_users_read_and_write_access](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_mount_Windows_partitions_.28NTFS.29_on_boot-up.2C_and_allow_users_read_and_write_access)

---

