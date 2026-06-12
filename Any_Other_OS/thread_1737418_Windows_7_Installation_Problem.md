---
title: "Windows 7 Installation Problem"
date: 2011-04-23
forum: Any Other OS
---

### Post by psycho5 on 2011-04-23
Hi, I'm trying to install Win 7 Pro 32bit, and the setup is unable to create a windows partition in the disk I want it to install.

I'm trying to install Windows on /dev/sdb where my previous windows (also windows 7) was installed. Setup keeps telling me windows is unable to install to that partition, check logs. 

```

$ sudo fdisk -l
[sudo] password for oj: 

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000df4ff

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         243     1951866   82  Linux swap / Solaris
/dev/sda2   *         244        2942    21674821   83  Linux
/dev/sda3            2942      121601   953133057    5  Extended
/dev/sda5            3891      121601   945512448    7  HPFS/NTFS

Disk /dev/sdb: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000c064c

   Device Boot      Start         End      Blocks   Id  System
oj@oj-desktop:~$

```

As you can see, /dev/sdb is blank, and I dunno why I can't proceed with the setup, I tested the win 7 on virtualbox and it installs fine, so what should i do?

---

### Post by psycho5 on 2011-04-23
Just had to physically disconnect the power to my ubuntu disk, then windows installed.. lol

---

