---
title: "Partition Sizes for a 40 GB drive"
date: 2006-08-25
forum: Absolute Beginner Talk
---

### Post by Metroid48 on 2006-08-25
Hi, I've got an external 40GB hard drive that I installed Ubuntu to. I originally made 1GB swap, 5 GB root, and left the rest as VFAT32 storage space. However, my root directory completely got filled and I've basically destroyed Ubuntu trying to fix that.

Anyway, just wondering what I should use for partitioning this time around. I would like a seperate root (/) and storage partitions, but that's just for ease of re-installation.

-Metroid48

---

### Post by Bachstelze on 2006-08-25
Go with 10 or even 15 GB for root, 512 MB or 1 GB swap depending on how much RAM you have and also a small /home (1 GB or so) to store some of your config files if you have to reinstall.

---

### Post by Metroid48 on 2006-08-25
How do you set the size for the /home directory?

Also, I've got 512 MB RAM.

---

### Post by Bachstelze on 2006-08-25
Just create another partition for your /home exactly the same way you do for your / except for the /home mountpoint.

I have 512 MB of RAM as well and I use 1 GB swap. Maybe it's a bit too much but hard drives are quite cheap nowadays :p

---

### Post by Metroid48 on 2006-11-04
Okay, I'm installing Edgy now but on my laptop's drive, which is 52 GB, while keeping Windows. I've only got 50% of the "C:" partition free, and would like storage space, so I'm thinking of only using 11 GB for my Ubuntu install. However, there's one weird thing. This is my current partitioning:

63MB FAT Dell Utilities|52GB NTFS Windows Install|3GB FAT32 Unknown

Anyway, I'm not sure if the Windows install is dependent on any of the other ones, and if I could just do this:

FAT|NTFS XP Install|10GB EXT3 Root|1GB EXT3 Home|600MB Swap|FAT32

Would that be safe?

---

