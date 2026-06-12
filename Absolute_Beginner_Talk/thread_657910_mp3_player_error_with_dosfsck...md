---
title: "mp3 player error with dosfsck.."
date: 2008-01-04
forum: Absolute Beginner Talk
---

### Post by hopelessone on 2008-01-04
Hi,

i went to delete some files and suddenly went to read only...ran this:

firebox@firebox-desktop:~$ dosfsck -a -v /dev/sdf
dosfsck 2.11 (12 Mar 2005)
dosfsck 2.11, 12 Mar 2005, FAT32, LFN
Currently, only 1 or 2 FATs are supported, not 191.

what do i do?

info:

Disk /dev/sdf: 4290 MB, 4290790400 bytes
32 heads, 63 sectors/track, 4156 cylinders
Units = cylinders of 2016 * 512 = 1032192 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdf1   *           1        4157     4190224+   6  FAT16


thanks..

---

