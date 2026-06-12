---
title: "hard drive conversion"
date: 2008-02-15
forum: Absolute Beginner Talk
---

### Post by TechDragon on 2008-02-15
Hi,

I have a 320gb external drive, that is formatted to ntfs.  For some reason I can not get it to mount in ubuntu.  I have tried everything I know to do...which is not much...asked for help and followed directions, but no luck.  Is there a tool to convert ntfs to something else without losing the data on it?

Thanks

---

### Post by Discov3ry on 2008-02-15
Did you have Windows installed on it before? Is it still installed?

---

### Post by jken146 on 2008-02-15
Please post the outputs of the following commands.

```
sudo fdisk -l
```

```
cat /etc/fstab
```

```
mount
```

---

### Post by dcstar on 2008-02-15
> **TechDragon said:**
> Hi,

I have a 320gb external drive, that is formatted to ntfs.  For some reason I can not get it to mount in ubuntu.  I have tried everything I know to do...which is not much...asked for help and followed directions, but no luck.  Is there a tool to convert ntfs to something else without losing the data on it?

Thanks

[http://ubuntuforums.org/showpost.php?p=4212634&postcount=3](http://ubuntuforums.org/showpost.php?p=4212634&postcount=3)

---

### Post by MasterJS on 2008-02-15
have you tried mounting it yourself through the terminal? type```
sudo fdisk -l
``` This will list all the hard drives and partitions. Once you've done this, your other hard drives main partition could be something like sda1, sdb1, or hdb1. Depending on which one it is, type ```
sudo mount /dev/**** /media/disk
``` this will mount it as /media/disk. Substitute the asterisks for the output of fdisk

---

### Post by TechDragon on 2008-02-16
weird, thank you all it started working.  It said it couldn't mount it.  I did the force command, it said it didn't mount it.  I ran the fdisk -l and it was listed so I went to the computer tab and it opened.

Thanks

---

