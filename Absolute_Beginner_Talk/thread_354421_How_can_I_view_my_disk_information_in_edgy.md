---
title: "How can I view my disk information in edgy?"
date: 2007-02-05
forum: Absolute Beginner Talk
---

### Post by Roasted on 2007-02-05
Since there's no disk manager in edgy that there was in dapper (at least, if there is, I don't see it) how can I view the disk info? For example, when I go to my /media folder, I see my 3 drives listed there. I have a network drive for the other computers, my backup drive which I normally keep unmounted, and my first drive. Now, my first drive displays as sda1, which from what I thought was my windows partition.

Where exactly is my linux partition? 


hdd1 = my IDE drive, which is the network drive.
sdb2 = my second SATA drive, which is strictly for backup purposes.
sda1 = from what I understood, sda1 was my windows partition.
So I guess that leaves sda3 as my linux partition? Where is it? Why can't I view it in media or anything?





   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3187    25599546    7  HPFS/NTFS
/dev/sda2            3188        3252      522112+  82  Linux swap / Solaris
/dev/sda3            3253       30515   218990047+  83  Linux

Disk /dev/sdb: 251.0 GB, 251000193024 bytes
255 heads, 63 sectors/track, 30515 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1          62      497983+   5  Extended
/dev/sdb2              63       30515   244613722+  83  Linux
/dev/sdb5               1          62      497952   82  Linux swap / Solaris

Disk /dev/hdd: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdd1   *           1       24792   199141708+  83  Linux
jason@jason:~$

---

### Post by muzzamo on 2007-02-06
If you are looking for a gui then gparted might be what you are looking for.
```

sudo apt-get install gparted

```

---

### Post by Roasted on 2007-02-06
Hahaha, nice. Under Applications-Accessories-Disk Usage Analyzer, it has the exact tool I was looking for. Imagine that? Only thing is this tool will ONLY tell me what sda3 is. If I mount sdb2 (backup drive) instead of displaying 2 drives, it seems to combine it together, making it difficult to know which one is full and which one isn't. Anybody know how I can list the drives separately? :confused: 

Thanks for the tip on gparted, it reminded me I have to install it anyway.

---

