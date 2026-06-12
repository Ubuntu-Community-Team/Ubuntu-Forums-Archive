---
title: "Using terminal to access hdd partitions"
date: 2007-11-27
forum: Absolute Beginner Talk
---

### Post by nemesis8601 on 2007-11-27
Is it possible to use the terminal to access other partitions? These partitions would be in FAT32 format. I can access these partitions on the desktop GUI, but not on the terminal. Is the terminal defaulted to only search through / files?

---

### Post by Inxsible on 2007-11-27
if you have those partitions mounted (which you probably do, since you can access them through the GUI) you can simply cd to those directories.
```
 cd /path/to/mount/point
```
```
ls -l
``` will list the files ```
ls-a
``` will show you the hidden files too

---

### Post by lespaul_rentals on 2007-11-27
Yes, you can.  If the device is mounted, you can just type

```
cd /mnt/device_name
```

...and it will go right to it.

---

### Post by nemesis8601 on 2007-11-27
Would the command be the same for NTFS partitions? These would have stored music and movies.

Thanks!

---

### Post by PeterJS on 2007-11-27
> **nemesis8601 said:**
> Would the command be the same for NTFS partitions? These would have stored music and movies.

Thanks!

That's the thing about the linux file system, the tools don't know the differnce. ls can't tell an ext3 file system, from fat32, from NTFS, from a cd (iso9660). Only the kernel knows about these differences. A mounted file system is amounted file system.

---

### Post by lespaul_rentals on 2007-11-28
> **nemesis8601 said:**
> Would the command be the same for NTFS partitions? These would have stored music and movies.

Thanks!

So long as the device has been mounted properly by the system, you should have no problem.

---

