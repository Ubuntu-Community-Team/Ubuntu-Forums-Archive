---
title: "New versions not in grub when installing Vista"
date: 2007-12-23
forum: Absolute Beginner Talk
---

### Post by Roger_Melly on 2007-12-23
Sorry,
I am fairly rubbish at this but I have just installed Vista and lost Grub.  I have downloaded an application called easyMBR (or something like that) and went through the Neo Grub thing.
I eventually got Ubuntu in the MBR as an option on startup but it's only an old version.  How do I add a newer version?
Thanks

---

### Post by Roger_Melly on 2007-12-23
Here is the result I get if I check my disks:
Disk /dev/hda: 122.9 GB, 122942324736 bytes
255 heads, 63 sectors/track, 14946 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        7916    63585238+   7  HPFS/NTFS
/dev/hda2            7917       11575    29390917+  83  Linux
/dev/hda3           14525       14946     3389715    5  Extended
/dev/hda4           11576       14524    23687842+  83  Linux
/dev/hda5           14658       14946     2321361   82  Linux swap / Solaris
/dev/hda6           14525       14657     1068259+  82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sda: 400.0 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       48641   390708801    7  HPFS/NTFS

---

