---
title: "Mount FAT32 in OSX"
date: 2008-06-13
forum: Apple Hardware Users
---

### Post by flyeng4 on 2008-06-13
Hi all,

I need help mounting my FAT32 partition when I boot to OSX. 
The partition is grayed out in Disk Utility and Verify says unrecognized disk format.
I installed MacFUSE and ntfs-3g. Still no luck. (I assume there is no set up to ntfs-3g)
I tried formating from Disk Utility while in OSX and it still will not mount.

I'm on the brink of insanity with this. This should be automatic. Please help. :)

- Ubuntu 8.04
- Macbook
- 3 Partitions
    1. OSX 
    2. FAT32 
    3. Ubuntu

---

### Post by cyberdork33 on 2008-06-13
do you have refit installed? If so, please post the output from the Partition Inspector in your Utilities folder.

---

### Post by flyeng4 on 2008-06-13
```

*** Report for internal hard disk ***

Current GPT partition table:
 #      Start LBA      End LBA  Type
 1             40       409639  EFI System (FAT)
 2         409640    102253724  Mac OS X HFS+
 3      167927445    172441709  Linux Swap
 4      172441710    234436544  Basic Data
 5      102253725    167927444  MS Reserved

Current MBR partition table:
 # A    Start LBA      End LBA  Type
 1              1       409639  ee  EFI Protective
 2         409640    102253724  af  Mac OS X HFS+
 3      167927445    172441709  82  Linux swap / Solaris
 4 *    172441710    234436544  83  Linux

MBR contents:
 Boot Code: Unknown, but bootable

Partition at LBA 40:
 Boot Code: None (Non-system disk message)
 File System: FAT32
 Listed in GPT as partition 1, type EFI System (FAT)

Partition at LBA 409640:
 Boot Code: None
 File System: HFS Extended (HFS+)
 Listed in GPT as partition 2, type Mac OS X HFS+
 Listed in MBR as partition 2, type af  Mac OS X HFS+

Partition at LBA 167927445:
 Boot Code: None
 File System: Unknown
 Listed in GPT as partition 3, type Linux Swap
 Listed in MBR as partition 3, type 82  Linux swap / Solaris

Partition at LBA 172441710:
 Boot Code: GRUB
 File System: ext3
 Listed in GPT as partition 4, type Basic Data
 Listed in MBR as partition 4, type 83  Linux, active

Partition at LBA 102253725:
 Boot Code: Unknown, but bootable
 File System: FAT32
 Listed in GPT as partition 5, type MS Reserved



```

---

### Post by cyberdork33 on 2008-06-13
it has the "Microsoft Reserved" flag set, which probably causes a problem.  See this:
[http://www.macosxhints.com/article.php?story=20080130022147512](http://www.macosxhints.com/article.php?story=20080130022147512)

PS. You actually have 5 partitions, not 3.


[LIST=1]
[*]EFI Partition
[*]OSX Partition (HFS+)
[*]swap partition (for ubuntu)
[*]Ubuntu Partition (ext3)
[*]Other partition (FAT32)
[/LIST]

---

