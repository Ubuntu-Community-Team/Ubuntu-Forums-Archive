---
title: "check disk"
date: 2006-10-29
forum: Absolute Beginner Talk
---

### Post by manfredell on 2006-10-29
What is the command or app to check the consistency of a disk (and repair errors) in Ubuntu, like chkdsk/f in Windows or the DiskUtility in Mac OSX??

Thx in advance

---

### Post by Bachstelze on 2006-10-29
```
(sudo) fsck -fy /dev/whatever
```

---

### Post by manfredell on 2006-10-29
> **HymnToLife said:**
> ```
(sudo) fsck -fy /dev/whatever
```

Thx,


Problem: what if I want to check my working partition which is mounted??

---

### Post by Najand on 2006-10-29
There are different commands in Linux with respect to your need, like:

fsck : check and repair a Linux file system
dosfsck : check and repair MS-DOS file systems
e2fsck : check a Linux ext2/ext3 file system
expiry : check and enforce password expiration policy
fsck.ext2 : check a Linux ext2/ext3 file system
fsck.ext3 : check a Linux ext2/ext3 file system
fsck.minix : a file system consistency checker for Linux
fsck.msdos : check and repair MS-DOS file systems
fsck.reiser4 : the program for checking and repairing reiser4 filesystem.
fsck.reiserfs : The checking tool for the ReiserFS filesystem.
fsck.vfat : check and repair MS-DOS file systems
hpfsck : check integrity of an HFS+ volume
reiserfsck : The checking tool for the ReiserFS filesystem.
xfs_check : check XFS filesystem consistency

---

### Post by xyz on 2006-10-29
You should not check a mounted partition.

---

### Post by Bachstelze on 2006-10-29
**@manfredell**, try to boot in "recovery mode", if I remember well, it forces filesystem checks during bootup.

---

### Post by xyz on 2006-10-29
Also this if you wish to change disk checking at boot:
```
sudo tune2fs -c 50 /dev/hdx@
```
50 means disk will be automatically checked at the 50th boot. Modify that number according to your wish/need.

---

### Post by Najand on 2006-10-29
Well, by changing the value of the 6th column in /etc/fstab from 0 to 1, will enable fsck during boot. fsck looks at the number in the 6th column to determine in which order the filesystems should be checked. If it's zero, fsck won't check the filesystem.

---

### Post by xyz on 2006-10-29
> **Najand said:**
> There are different commands in Linux with respect to your need, like:

fsck : check and repair a Linux file system
dosfsck : check and repair MS-DOS file systems
e2fsck : check a Linux ext2/ext3 file system
expiry : check and enforce password expiration policy
fsck.ext2 : check a Linux ext2/ext3 file system
fsck.ext3 : check a Linux ext2/ext3 file system
fsck.minix : a file system consistency checker for Linux
fsck.msdos : check and repair MS-DOS file systems
fsck.reiser4 : the program for checking and repairing reiser4 filesystem.
fsck.reiserfs : The checking tool for the ReiserFS filesystem.
fsck.vfat : check and repair MS-DOS file systems
hpfsck : check integrity of an HFS+ volume
reiserfsck : The checking tool for the ReiserFS filesystem.
xfs_check : check XFS filesystem consistency


Thanks Najand for posting this!

---

### Post by CatKiller on 2006-11-04
> **manfredell said:**
> Problem: what if I want to check my working partition which is mounted??

```
sudo touch /forcefsck
``` and then reboot.

EDIT: You might need to remove the /forcefsck directory once you've rebooted - I can't remember if it happens automatically or not.

---

