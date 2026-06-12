---
title: "e2fsck"
date: 2007-03-14
forum: Absolute Beginner Talk
---

### Post by Blofeld on 2007-03-14
Hey, I can't get my head 'round e2fsck, so here are some general / newbie questions:
* do I need e2fsck on an ext3 file system at all, or can I switch it off?
* am I right in the assumption that if I want to run e2fsck on my hard disk, I will have to do so via a live CD or a floppy disk as I can't very well umount the root partition?  Or is there a way to run e2fsck when the computer reboots (and before the root partition has been mounted)?
Thanks.

---

### Post by mcduck on 2007-03-14
1. Yes, you should run fsck on ext3 partitions every now and then
2. By default, fsck is run for partitions after every 30 mounts at the boot time. So you should not need to run it yourself.

---

### Post by xyz on 2007-03-14
Yi you want you can decide to set up check disk number option at boot:
run
```
sudo tune2fs -c 50 /dev/hdx
```
change  50  to whatever you want...and hdx to your partition to be checked.

---

### Post by Blofeld on 2007-03-14
Exellent and most helpful answers, thanks, duckies!

---

### Post by Blofeld on 2007-03-14
... and another thing, I have found out that you can force Linux to check all partitions during the next boot by commanding ```
sudo touch /forcefsck
``` and then restarting the system (obviously).
This enables you to check the file system on the root partition without having to boot from an external medium.
Sweet.

---

### Post by xyz on 2007-03-14
> **Blofeld said:**
> ... and another thing, I have found out that you can force Linux to check all partitions during the next boot by commanding ```
sudo touch /forcefsck
``` and then restarting the system (obviously).
This enables you to check the file system on the root partition without having to boot from an external medium.
Sweet.
That'll sure do it at next boot!
Here is some more using GParted Live or a Live CD as root:

**Running a filesystem check on a FAT32  filesystem**

```
root@GParted:~# fsck.vfat -a -l -v /dev/hda1 (yours may not be 1)
```
  
**Running a filesystem check on an ext3  filesystem**  
  
```
 root@GParted:~# e2fsck -C0 -p -f -v /dev/hda2
```
Where: hda2 is the ext3 partition to be checked.

---

