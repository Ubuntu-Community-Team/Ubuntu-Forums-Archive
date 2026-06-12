---
title: "file permission for 2nd hdd"
date: 2007-03-19
forum: Absolute Beginner Talk
---

### Post by pirata on 2007-03-19
When I switched to Ubuntu from windows I wanted to maintain the same set up I had, which was to have a small (20Gb) hard drive with the operating system installed on it and a larger (180) hdd for all my word files, movies, music etc. I installed Ubuntu on my small hdd and mounted the second one (see below for file system info). I can access the files but they are read only so I can't edit them and I can't save new files on this drive, which I need to continue doing. Please can someone tell me how to set this up so I can easily edit and save new files onto this drive? Cheers...  

<file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdb1   /media/hdb1   ntfs   nls=utf8,umask=0222   0   0
 
Disk /dev/hda: 20.4 GB, 20496236544 bytes
255 heads, 63 sectors/track, 2491 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        2398    19261903+  83  Linux
/dev/hda2            2399        2491      747022+   5  Extended
/dev/hda5            2399        2491      746991   82  Linux swap / Solaris

Disk /dev/hdb: 122.9 GB, 122942324736 bytes
255 heads, 63 sectors/track, 14946 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1       14946   120053713+   7  HPFS/NTFS

Disk /dev/sda: 1048 MB, 1048576000 bytes
32 heads, 63 sectors/track, 1015 cylinders
Units = cylinders of 2016 * 512 = 1032192 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1014     1022080+   6  FAT16

---

### Post by Zzl1xndd on 2007-03-19
looks like you have the 2nd HD set up with the NTFS file system. Ubuntu normally will read the file system but has issues writing to it. 

this should help [http://ubuntuforums.org/showthread.php?t=217009](http://ubuntuforums.org/showthread.php?t=217009)

---

### Post by dfreer on 2007-03-19
Congrats! This is definitely a good idea, whether using windows or ubuntu. I wish more people would do this instead of lumping everything onto one HD.

> /dev/hdb1 * 1 14946 120053713+ 7 HPFS/NTFS

Here's your main problem. Linux at the current time can only (safely and reliable) read NTFS, and cannot write to it without installing special programs (see [*_this thread_*]("http://www.ubuntuforums.org/showthread.php?t=217009")). Even with that installed I wouldn't be willing to risk data corruption... Your best bet is to make that partition FAT32 (if you want it to be readable/writable by windows), or ReiserFS (or whatever native linux partition makes your heart go flippity-flop). 
  Once you do that (make sure to transfer any important data off of it first...), if you are still having read/write problems let us know.

EDIT: Link to thread that I posted is the same thread as the post above.

---

