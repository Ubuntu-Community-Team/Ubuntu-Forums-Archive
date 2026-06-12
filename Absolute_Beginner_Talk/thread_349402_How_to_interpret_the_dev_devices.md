---
title: "How to interpret the /dev/ devices"
date: 2007-01-30
forum: Absolute Beginner Talk
---

### Post by btrotter on 2007-01-30
I am trying to make sense of the /dev devices, and my previous understanding is with windows.

I know for instance that a hard disk is going to be something like /dev/sda, and the cdrom will be /dev/cdrom, but I dont really know how to tell what else I have, and especially with the hard disks, how do I know which hard disk is mapped to which /dev/sdX?

For instance, in Windows (or DOS), if I wanted to know which hard disks are installed, I would run fdisk, and I could see for instance that I have 2 hard disks installed, and 1 hard disk had 2 partitions on it (C & D), and the other has 3 (E, F & G).

If I run a "fdisk -l" in Linux, I see a lot of /sda1, /sda2, sda3, but those just seem to be the partitions that are set up...not the drives/devices that are installed. For example, where do I go to find out what sda is, and what sdb is? Then how do I find out what else is installed besides /dev/sda, /dev/cdrom, etc?

Thanks for your help in making my world a brighter day being without Windows. :)

---

### Post by cwaldbieser on 2007-01-30
> **btrotter said:**
> I am trying to make sense of the /dev devices, and my previous understanding is with windows.

I know for instance that a hard disk is going to be something like /dev/sda, and the cdrom will be /dev/cdrom, but I dont really know how to tell what else I have, and especially with the hard disks, how do I know which hard disk is mapped to which /dev/sdX?

For instance, in Windows (or DOS), if I wanted to know which hard disks are installed, I would run fdisk, and I could see for instance that I have 2 hard disks installed, and 1 hard disk had 2 partitions on it (C & D), and the other has 3 (E, F & G).

If I run a "fdisk -l" in Linux, I see a lot of /sda1, /sda2, sda3, but those just seem to be the partitions that are set up...not the drives/devices that are installed. For example, where do I go to find out what sda is, and what sdb is? Then how do I find out what else is installed besides /dev/sda, /dev/cdrom, etc?

Thanks for your help in making my world a brighter day being without Windows. :)

"lshw" and "discover" might help you find out about installed hardware.  "mount" used without any options will tell you what your currently mounted filesystems are and what devices they correspond to.  There are also so graphical tools reminicent of the Windows device manager in the System menu.

---

### Post by p!=f on 2007-01-30
If I understand correctly you want to know how your patitions (/dev/hdax, /dev/sdax, ...) are mounted.
Instead of looking at /dev/ look at /proc
```

cat /proc/partitions
cat /proc/mounts

```
or
```

mount
cat /etc/fstab

```
that shows you current mounts with their mount points.

Hope it helps.

---

### Post by steve.horsley on 2007-01-30
The hd drives are:
hda - first IDE cable master
hdb - first IDE cable slave
hdc - second IDE cable master
hdd - second IDE cable slave

the sda drives are more difficult. sd used to be for SCSI drives. USB disks are emulated as SCSI disks by the drivers, and so, I think, are SATA drives.

You can find a bit more by looking in /sys/block. I've got an hda in there, and it looks like this:
> steve@Dingly:~$ ls -l /sys/block/hda
total 0
-r--r--r-- 1 root root 4096 2007-01-30 12:52 dev
lrwxrwxrwx 1 root root    0 2007-01-30 12:52 device -> ../../devices/pci0000:00/0000:00:1f.1/ide0/0.0
drwxr-xr-x 3 root root    0 2007-01-30 12:53 hda1
drwxr-xr-x 3 root root    0 2007-01-30 08:21 hda2
drwxr-xr-x 3 root root    0 2007-01-30 08:21 hda3
drwxr-xr-x 3 root root    0 2007-01-30 08:21 hda5
drwxr-xr-x 3 root root    0 2007-01-30 08:21 hda6
drwxr-xr-x 3 root root    0 2007-01-30 08:21 hda7
drwxr-xr-x 3 root root    0 2007-01-30 08:21 hda8
drwxr-xr-x 3 root root    0 2007-01-30 08:20 hda9
drwxr-xr-x 2 root root    0 2007-01-30 08:20 holders
drwxr-xr-x 3 root root    0 2007-01-30 08:20 queue
-r--r--r-- 1 root root 4096 2007-01-30 12:52 range
-r--r--r-- 1 root root 4096 2007-01-30 12:52 removable
-r--r--r-- 1 root root 4096 2007-01-30 12:52 size
drwxr-xr-x 2 root root    0 2007-01-30 08:20 slaves
-r--r--r-- 1 root root 4096 2007-01-30 12:52 stat
--w------- 1 root root 4096 2007-01-30 12:52 uevent

You can see there's a PCI address hidden in there. Most of those files can be read out and provide info. e.g. 
> steve@Dingly:~$ cat /sys/block/hda/range
64


For other types of devices, I really don't know. Googling will find you lots of stuff, but it may be difficult to understand.

The number after the drive name gives the partition number on the disk. So you can see my hda has 8 partitions, 1-9 excluding 4. fdisk tells you this too.

P.S.
> cat /proc/partitions
cat /proc/mounts
nice one, p!=f

---

### Post by btrotter on 2007-01-30
Excellent tips!
Thanks guys!!!!!

---

