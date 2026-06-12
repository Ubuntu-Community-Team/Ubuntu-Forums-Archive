---
title: "Mounting a GPT filesystem"
date: 2008-10-31
forum: Apple Hardware Users
---

### Post by Konstabel on 2008-10-31
How can I mount the following file system in Ubuntu?

GPT (GUID Partition Table) detected on '/dev/sdb'! The util fdisk doesn't support GPT. Use GNU Parted.

Thanks

---

### Post by Frak on 2008-10-31
For what use?

For install, it should already be mounted.

For use in Ubuntu... it should already be mounted.

---

### Post by cyberdork33 on 2008-11-01
> **Konstabel said:**
> How can I mount the following file system in Ubuntu?

GPT (GUID Partition Table) detected on '/dev/sdb'! The util fdisk doesn't support GPT. Use GNU Parted.

Thanks

You are confusing terminology. A file system is a method of storing files on a partition. Examples of filesystems are ext3 (Linux), HFS+ (OS X), and NTFS (Windows).

The GUID Partition System is a method of indicating the size and position of hard disk partitions. You do not "mount" a partition table, you mount a filesystem.


Please tell us exactly what you are trying to do and we can help you accomplish what you are trying to.

---

### Post by Konstabel on 2008-11-01
I am borrowing a friend's HFS+ formatted external usb harddrive from which I would like to copy some stuff. But I cannot get it mounted. And cannot seem to find a way to do it either.

---

### Post by TheProphetJonah on 2010-02-06
So I'm having much the same problem. I installed cAos on an empty disk, hdb.
It shows in fdisk as being 

> /dev/hdb1 * 1   3650 29316671+ ee EFI GPT
that being Device, Boot, Start End Blocks Id System

cAos allegedly installed a bootloader. Perhaps. Meanwhile, I don't have anything else booting so I'm running this from a Puppy Linux disk. My other partitions are there.

I was about to kludge in a GRUB or better yet LiLo bootloader (yeah, I know, GRUB BEST! GRUB BEST! and all that but older versions of GRUB have a little problem with the uuid instead of root kopt) but it shows up as mentioned above. 

I'm wondering if GRUB will recognize it. Puppy Pdrive drive manager doesn't show it.

cAos because I've got enough mainboards with CPUs and memory that I'm trying, for my first time, to run a Beowulf. And cAos has on the install DVD a system tool called WareWulf (if English isn't your first language, I should explain that the name is a really bad pun. Thank God, I'm not the one responsible for it.)

I'm also wondering if Karmic will play nice with the new baby. I've been having a lot of trouble trying to add Mandriva 2010 to the boot order as well.

---

### Post by warrenc5 on 2011-06-04
You need to have EFI GUUID Partition Support enabled in the kernel 

zcat /proc/config.gz | grep EFI_PARTITION
# CONFIG_EFI_PARTITION is not set

---

