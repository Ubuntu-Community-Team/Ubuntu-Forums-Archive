---
title: "[SOLVED] partitions"
date: 2007-09-15
forum: Absolute Beginner Talk
---

### Post by skyjacker on 2007-09-15
Just curious, i installed Fiesty and used the first option (use available space) to create partitions. here is what i have.
Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *         490        4137    29302560    7  HPFS/NTFS
/dev/hda2               1         489     3927861    b  W95 FAT32
/dev/hda3            4138        9565    43600410   83  Linux
/dev/hda4            9566        9729     1317330    5  Extended
/dev/hda5            9566        9729     1317298+  82  Linux swap / Solaris
Could someone tell me what hda 3 and hda 4 are? I think 1 and 2 are M$S partitions , as I dual boot
Thanks

---

### Post by skymera on 2007-09-15
hda1 = NTFS windows
hda2 = FAT32 windows
hda3 - linux i think its EXT3
hda4 = extended partiiton contains...
hda5 = swap

---

### Post by SpiritIsReality on 2007-09-15
howdy
in advanced search, search partitioning basics, titles only, tutorials and tips forum
[http://ubuntuforums.org/showthread.php?t=282018&highlight=partitioning+basics](http://ubuntuforums.org/showthread.php?t=282018&highlight=partitioning+basics)

trails

---

### Post by skyjacker on 2007-09-15
> **fmat said:**
> howdy
in advanced search, search partitioning basics, titles only, tutorials and tips forum
[http://ubuntuforums.org/showthread.php?t=282018&highlight=partitioning+basics](http://ubuntuforums.org/showthread.php?t=282018&highlight=partitioning+basics)

trails   Thanks for the link---lots of good info there.:):)

---

