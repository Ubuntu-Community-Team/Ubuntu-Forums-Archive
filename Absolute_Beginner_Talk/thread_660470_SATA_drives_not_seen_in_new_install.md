---
title: "SATA drives not seen in new install"
date: 2008-01-06
forum: Absolute Beginner Talk
---

### Post by ThunderRd on 2008-01-06
I have installed 7.04 and am a new user. I have spent some time feeling my way around the OS and have discovered how to view the drives in other computers on my home LAN. I can see the contents of both IDE and SATA drives on the other machines, but I can't access either of the SATA driuves on the local machine, the one with Ubuntu. I need to access those drives, at least read-only, in Linux.

This machine is in a dual boot with XP. XP on the primary master, Ubuntu on the primary slave. All the windows partitions are NTFS. The two SATA drives are NTFS also, and contain mp3 files that I wish to play in Ubuntu.

I can provide whatever info is needed.

---

### Post by Blutack on 2008-01-06
Could you please paste the output of
```
sudo fdisk -l
```
I know it looks really bad but all it does is list your known partitions.  Typing
```
man fdisk
```
and having a quick read should alleviate your fears.

---

### Post by Toxicity999 on 2008-01-06
I'm not sure what the actual problem is, you can't access partitions on your local machine? If they were there at install, they should be audio discovered, and seen in 'Computer' (If using gnome). If they are not, you have to find the dev location and mount it manually.

These will generally be in the form of sdaX where x is the partition number, starting at 1, and a is the alphabet corresponding to drive dominance, ie sda sdb.

Then you're looking at some reading:
man mount

You're looking to make a directory, then mount the /dev/sd* as ntfs.

---

### Post by ThunderRd on 2008-01-06
> **Blutack said:**
> Could you please paste the output of
```
sudo fdisk -l
```
I know it looks really bad but all it does is list your known partitions.  Typing
```
man fdisk
```
and having a quick read should alleviate your fears.

I see only /hda and /hdb in fdisk:

```

Disk /dev/hda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Device    Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        1530    12289693+   7  HPFS/NTFS
/dev/hda2            1531        4865    26788387+   7  HPFS/NTFS

Disk /dev/hdb: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Device    Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        4660    37431418+  83  Linux
/dev/hdb2            4661        4865     1646662+   5  Extended
/dev/hdb5            4661        4865     1646631   82  Linux swap / Solaris

```

I think that this is the problem:
> If they were there at install, they should be audio discovered, and seen in 'Computer' (If using gnome). If they are not, you have to find the dev location and mount it manually.

They weren't, and I didn't do this.  Can you help me to get started finding the locations?

---

