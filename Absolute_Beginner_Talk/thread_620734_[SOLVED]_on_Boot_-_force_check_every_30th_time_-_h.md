---
title: "[SOLVED] on Boot - force check every 30th time - how to change?"
date: 2007-11-22
forum: Absolute Beginner Talk
---

### Post by MozartlovesUbun2 on 2007-11-22
went though some posts and

**i tried these, but why does it say can't find!**

mozart@network:~$ sudo su
root@network:/home/mozart# tune2fs -c 100 -i 3m /dev/hda1
tune2fs 1.40.2 (12-Jul-2007)
tune2fs: No such file or directory while trying to open /dev/hda1
Couldn't find valid filesystem superblock.
root@network:/home/mozart# tune2fs -c 100 -i 3m /dev/hda2
tune2fs 1.40.2 (12-Jul-2007)
tune2fs: No such file or directory while trying to open /dev/hda2
Couldn't find valid filesystem superblock.
root@network:/home/mozart# tune2fs -l /dev/hda1
tune2fs 1.40.2 (12-Jul-2007)
tune2fs: No such file or directory while trying to open /dev/hda1
Couldn't find valid filesystem superblock.
root@network:/home/mozart# sudo tune2fs -c 100 /dev/hda1
tune2fs 1.40.2 (12-Jul-2007)
tune2fs: No such file or directory while trying to open /dev/hda1
Couldn't find valid filesystem superblock.
root@network:/home/mozart# 

**so how do I make it check on every 100th boot or better even that it checks on sgut down**

---

### Post by LaRoza on 2007-11-22
Try changing the "hda" to "sda".

---

### Post by AusIV4 on 2007-11-23
To find out what the device name is, run:```
sudo fdisk -l
```But instead of changing to 100 mounts (plenty of time to be corrupted), I'd recommend installing [AutoFsck](https://wiki.ubuntu.com/AutoFsck) to make file system checks happen on your schedule, rather than an arbitrary boot count.

---

### Post by bluepowder7 on 2007-11-23
just out of curiosity, which filesystems are exempt from having to be checked every so often?  are there any, actually, or do they ALL (ext2/3, reiser, jfs, xfs, and whatever else) need to be checked periodically?

---

### Post by MrFSL on 2007-11-23
File system checks  can be effected by the file: /etc/fstab

For more information:
```
man fstab
```

---

### Post by stchman on 2007-11-23
I have found that the fsck only does its thing on the partition that Ubuntu is on.

I keep my Ubuntu "/" partition in the order of 30G in size and don't put any of my personal stuff on it.

This keeps the auto check every 30th boot to a minimal time.

---

### Post by LaRoza on 2007-11-23
> **stchman said:**
> I have found that the fsck only does its thing on the partition that Ubuntu is on.

It depends on fstab.

---

### Post by MozartlovesUbun2 on 2007-11-23
> **LaRoza said:**
> Try changing the "hda" to "sda".

Yes thank you very much, that worked

**sudo tune2fs -c 100 /dev/sda1**

---

