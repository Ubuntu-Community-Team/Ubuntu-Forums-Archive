---
title: "How to mount fat32 into the /home directory...?"
date: 2007-01-20
forum: Absolute Beginner Talk
---

### Post by knemir on 2007-01-20
Hi everyone,

I have no much experience in Ubuntu, but I would like to know if it is possible to mount fat32 partition into the /home/user_name/some_folder ? Actually I managed to do that, but than I didn't have permission to write in that folder (some_folder). I tried to play with chmod and stuffs like that, but obviously I don't know how to do that! Also, should I change something in fstab file? I would appreciate if anyone helps...  Thanks in advance...

---

### Post by K.Mandla on 2007-01-21
(Moved to Absolute Beginner Talk. ;) )

---

### Post by iver2435 on 2007-01-21
sudo mount -t fat32 <partitionname> /home

For partition name, it can vary from system to system, but it usually looks something like:

/dev/hda2  (or something similar)

If you go into Hardware Manager, you can view all the hard drives and their partition names and decide which one to use.

---

### Post by Bachstelze on 2007-01-21
First, the -t value for FAT32 is *vfat*.

Second, you need to pass some extra parameters to your mount command to have write access to the partition, since FAT32 can't handle file permissions. Everything you need is explained [here](https://wiki.ubuntu.com/MountingWindowsPartitions).

---

