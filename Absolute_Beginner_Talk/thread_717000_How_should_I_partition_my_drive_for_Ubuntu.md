---
title: "How should I partition my drive for Ubuntu"
date: 2008-03-06
forum: Absolute Beginner Talk
---

### Post by kcav45 on 2008-03-06
Would like advice about my propossed strategy for partitioning and formating disks for Ubuntu 7.10 "Gutsy Gibbon"; have notebook with 60GB internal hard drive, and a 300GB external hard drive that will be shared with notebooks running Windows XP"'

**Internal Drive**

I think keeping system files and application programs seperate from my data files would fasciltate clean operation, particularly clean installs/uninstalls;  so on my system disk C: I plan to create three directories: /GG (for Gutsy Gibbon progams), /Program Filess (for third party programs), and  /home for user settings. I would create subfolders for each application package, and for each user, and have a directory called All Users.  Please advise, is this a good idea? 

I would format the entire hard drive to EXT3 except for a 3GB disk partition for the Swap file; I would name it drive S and format it to FAT32 (system has have 2GB RAM).

Have no idea how much disk space would be left after installing and configuring Ubuntu and my apps this way, but it would be interesting to see, and to estimate the distribution of different size data files I might generate in six months of normal operation. 

**External Drive**

Format the external hard drive to Ext32; use FS-Drive  program to allow Windows to read from and write to Ext3 partitions. So FAT32 can go out the window—none of the limitations of FAT32 (no file permissions, lots of fragmentation, and a file size limit of 4 GB).  The data trasfer rate to an eSATA drive is 4.5GB/S.

How can I fix the assignment of drive letter M to the external hard drive?

KC

---

### Post by prshah on 2008-03-06
60 Gb: 3 partitions (4 if you want to dualboot Windows) (all primary)

Partition 1: (if you want windows)
20Gb NTFS

Partition 2: mount point "/"
10Gb EXT3

Partition 3: swap space
1Gb swap (no need for 3Gb if you have system RAM of 2Gb, but if you want 3Gb, go ahead)

Partition 4: mount point "/home"
All the rest of the space.

If you do not want to dual boot Windows, you can eliminate partition 1.

External drive: better make it NTFS (readable/writeable out of the box with Ubuntu 7.10).
2/3 partitions as per your choice; partitioning will make it easier to defrag.

Cheers,
PRShah

---

### Post by herbster on 2008-03-06
You won't be creating directories, you'll be creating partitions.

I think you're overthinking the process a bit as well as just a general misunderstanding. The simplest concept is to have your internal drive in 4 partitions: One NTFS/FAT for XP, one for your root, one for your home and one for swap. How much RAM do you have? This will impact what you need for your swap. You can do something like 30gb XP, 8gb root, 2gb swap and 20gb home-- pretty safe bet all-around.

The drive letter assignment using FS driver is in Control Panel > IFS Drives and there you will see your ext3 drive, hit the drop-down box and choose a letter. Bingo bango.

---

### Post by justin whitaker on 2008-03-06
> **kcav45 said:**
> 
**Internal Drive**

I think keeping system files and application programs seperate from my data files would fasciltate clean operation, particularly clean installs/uninstalls;  so on my system disk C: I plan to create three directories: /GG (for Gutsy Gibbon progams), /Program Filess (for third party programs), and  /home for user settings. I would create subfolders for each application package, and for each user, and have a directory called All Users.  Please advise, is this a good idea? 

Not really. There is a syntax/vocabulary issue here. You are talking about creating partitions, not folders. Think of them as logical walls around XP land and Ubuntu Land. 

> I would format the entire hard drive to EXT3 except for a 3GB disk partition for the Swap file; I would name it drive S and format it to FAT32 (system has have 2GB RAM).

XP won't run on EXT3. You will need a separate partition in NTFS format if you want an XP install (and you probably should have one, just in case.)

> Have no idea how much disk space would be left after installing and configuring Ubuntu and my apps this way, but it would be interesting to see, and to estimate the distribution of different size data files I might generate in six months of normal operation. 

The core Ubuntu install is <2gb. Once you start installing more apps, it could conceivably grow to 5-10gb in size just for the OS, although you will have to install a helluva lot of applications to get there. 

> Format the external hard drive to Ext32; use FS-Drive  program to allow Windows to read from and write to Ext3 partitions. So FAT32 can go out the window—none of the limitations of FAT32 (no file permissions, lots of fragmentation, and a file size limit of 4 GB).  The data trasfer rate to an eSATA drive is 4.5GB/S.

Leave your external drive formatted NTFS, and use Ubuntu's NTFS driver to read/write to it. 

Your best bet is to partition your drives as prshah suggested. That's a pretty sane setup.

---

