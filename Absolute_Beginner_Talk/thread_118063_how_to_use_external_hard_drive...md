---
title: "how to use external hard drive.."
date: 2006-01-16
forum: Absolute Beginner Talk
---

### Post by grim918 on 2006-01-16
i have an external hard drive that i want to use with with ubuntu but i have no idea how to use it. ubuntu recognizes the drive but i dont know how to do anything with it. i cant create any directories or files. i just have no idea how to use the drive. can someone help me out on how to use an external hdd. i would appreciate any help

---

### Post by kont.raen on 2006-01-16
[QUOTE=grim918]i have an external hard drive that i want to use with with ubuntu but i have no idea how to use it. ubuntu recognizes the drive but i dont know how to do anything with it. i cant create any directories or files. i just have no idea how to use the drive. can someone help me out on how to use an external hdd. i would appreciate any help[/QUOTE]

Hello grim918,

well you said that the drive has been recognized by Ubuntu - but what would be necessary to help you is an information on wether there are already partitions on that drive or not.

If not, then you should create them with parted (terminal-app) or gparted (GUI-app) - whereas the latter one is not installed by default iirc - so you would have to fetch it with synaptic. If, on the other hand there are existing partitions, then you will have to add mountpoints and entries in the /etc/fstab so that you can  mount them - try an

sudo fdisk -l /dev/name-of-the-device-as-which-your-drive-is-recognized

Presuming the external drive is USB or FireWire, it probably is something like sda, sdb or the like.

Alright - I hope that serve's as a starter - if there are any further questions - just ask ;)

---

### Post by grim918 on 2006-01-17
the drive does have partitions in it. how do i add the mount points and entries into the /etc/fstab. im new to linux. thank you for your help

---

### Post by stfu on 2006-01-18
[QUOTE=grim918]the drive does have partitions in it. how do i add the mount points and entries into the /etc/fstab. im new to linux. thank you for your help[/QUOTE]
Depending on the filesystem that is used you can manually mount the partitions via disks-admin (GUI). If the filesystem is NTFS you cannot write any data on the disk even if you mount it.

fstab could be something like this:

```

/dev/sda1  /mnt/ntfs  ntfs  ro  0 0

```
It mounts the device /dev/sda1 into directory /mnt/ntfs on every boot with "read only" switch. You have to manually create the directory you want to mount the device/partition into.

---

