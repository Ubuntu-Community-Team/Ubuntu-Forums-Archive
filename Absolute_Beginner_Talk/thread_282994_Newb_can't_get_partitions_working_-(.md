---
title: "Newb can't get partitions working :-("
date: 2006-10-23
forum: Absolute Beginner Talk
---

### Post by IsaacJ on 2006-10-23
Hello all.  I am a total newb to Linux, but I am a pretty advanced Windows user who knows how to do most of this stuff for Windows.  (This is of some use, but not a lot here)

Since I don't want Windows Vista, I decided to finally install Ubuntu like I'd planned months ago.  But neither the 6.06 or the older 5.10 disks can partition/format my drives to do the install.  ](*,)  Windows has no trouble manipulating partitions on the drive.

I actually have 3 hard drives (2 IDE and 1 SATA).  Since I installed the SATA drive after the 2 IDEs, my current Windows XP install is on a different drive than the one I want to use, which is the SATA.  I've made room in the first 2 partitions so I can install Linux in one (E: on WinXP) and a FAT32 (H: on WinXP).  But whenever I try, the partition manager on both Ubuntu 5.10 and 6.06 fails at both.  I have tried deleting the parts, which it is able to do, then going back and formatting them the way I want (including a 2 gig Swap File for Ubuntu) but it still fails during the format.  There are 2 other NTFS partitions on the drive that I want to keep.  The ones I want to use for Linux show up in WinXP Disk Management as the first two partitions.  Under Linux, they are sda 1 and sda 5.

I'm a newb with the partition manager here, so I could certainly be something dumb that I don't know about.  :confused: 

Any help would be great.  Thanks a lot for your time.

---

### Post by ReaderRat on 2006-10-23
Give this a read....may cause problems...
[**Mixing PATA/SATA Drives**](http://ubuntuforums.org/showthread.php?t=204428)

---

