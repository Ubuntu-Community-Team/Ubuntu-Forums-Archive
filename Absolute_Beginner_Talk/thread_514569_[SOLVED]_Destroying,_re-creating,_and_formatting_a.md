---
title: "[SOLVED] Destroying, re-creating, and formatting a partition in GParted doesn't erase"
date: 2007-07-31
forum: Absolute Beginner Talk
---

### Post by Shadow ZERO on 2007-07-31
In an effort to make a more permanent switch to Linux, i recently decided to back up all the data on my main storage drive, and re-partition and format it in an ext3 file system.  The drive was previously NTFS, but it never had an OS on it.

After backing up all my data to an external USB drive, i proceeded to use GParted to destroy the NTFS partition, and created a single primary ext3 file system.  I then used GParted to format the partition in ext3 as well.

Here's whats boggling me.  Even after destroying the original partition and completely re-creating AND formatting it with an entirely different file system, the data is still readable through Linux.  GParted reads the drive as ext3 now, but there are still 2 partitions of the exact same size as they were when it was NTFS.  The % of space being used on the drive is also the same as when it was NTFS.

I don't really trust the integrity of the data on my storage drive anymore.  Although it seems to read fine for now, i have no idea how that is possible.  Obviously GParted is leaving the data on the drive intact to some extent, i was looking to return the drive into a state as if it was brand new (even if i have to low-level format).  How would i go about doing this?

---

### Post by jfinkels on 2007-07-31
> **Shadow ZERO said:**
> In an effort to make a more permanent switch to Linux, i recently decided to back up all the data on my main storage drive, and re-partition and format it in an ext3 file system.  The drive was previously NTFS, but it never had an OS on it.

After backing up all my data to an external USB drive, i proceeded to use GParted to destroy the NTFS partition, and created a single primary ext3 file system.  I then used GParted to format the partition in ext3 as well.

Here's whats boggling me.  Even after destroying the original partition and completely re-creating AND formatting it with an entirely different file system, the data is still readable through Linux.  GParted reads the drive as ext3 now, but there are still 2 partitions of the exact same size as they were when it was NTFS.  The % of space being used on the drive is also the same as when it was NTFS.

I don't really trust the integrity of the data on my storage drive anymore.  Although it seems to read fine for now, i have no idea how that is possible.  Obviously GParted is leaving the data on the drive intact to some extent, i was looking to return the drive into a state as if it was brand new (even if i have to low-level format).  How would i go about doing this?

Are you certain that the partition was reformatted? What is the output of this command?```
sudo fdisk -l
``` You can check the filesystem usage of a particular device by using the program 'df' like so:```
df /dev/sda1
``` where /dev/sda1 is the name of the partition you want to check. Or you can use 'df' without any parameters to view all filesystem usages.

Further questions: can you mount the partition that you supposedly have overwritten as ext3?

If you really want to wipe a hard drive or a partition (write all bits as 0 or any arbitrary string) you can use the ultimate boot CD [http://www.ultimatebootcd.com/](http://www.ultimatebootcd.com/)

---

