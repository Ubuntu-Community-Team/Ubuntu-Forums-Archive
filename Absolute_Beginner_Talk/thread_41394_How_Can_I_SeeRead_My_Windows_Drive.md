---
title: "How Can I See/Read My Windows Drive?"
date: 2005-06-13
forum: Absolute Beginner Talk
---

### Post by halfpower on 2005-06-13
I have two hard drives.  I have one for Windows (2 partitions) and another for Ubuntu.  I've just installed Ubuntu on the other.  Can anyone tell me how I can see and read data from my Windows drive?  Can I safely write data to my Windows drive if the drive is not FAT32?

many thanks
halfpower

---

### Post by ubuntu_demon on 2005-06-13
[http://ubuntuguide.org/#windows](http://ubuntuguide.org/#windows) :)

If you want to share a partition with windows AND be able to write you should use fat32

---

### Post by jeroevi on 2005-06-13
[QUOTE=halfpower]I have two hard drives.  I have one for Windows (2 partitions) and another for Ubuntu.  I've just installed Ubuntu on the other.  Can anyone tell me how I can see and read data from my Windows drive?  [/QUOTE]

You need to add the the windows drives to /etc/fstab
see: [http://www.ubuntuguide.org/#windows](http://www.ubuntuguide.org/#windows)

[QUOTE=halfpower]Can I safely write data to my Windows drive if the drive is not FAT32? [/QUOTE]

Writing to FAT32 works very well.
Writing to NTFS is experimental.

jeroen

---

### Post by somuchfortheafter on 2005-06-13
the last that i remember you can write to an ntfs drive as long as you dont change the file size or the name... this only works well for small registry tweaks but hey its a start right?

---

### Post by poofyhairguy on 2005-06-13
[QUOTE=halfpower] Can I safely write data to my Windows drive if the drive is not FAT32?
[/QUOTE]

No. You can read NTFS all day long, but writing to NTFS is disabled because it could easily destroy your data. If you need to do that, you must convert your old drive to FAT.

---

### Post by wylfing on 2005-06-13
[QUOTE=poofyhairguy]If you need to do that, you must convert your old drive to FAT[/QUOTE]
...and the only foolproof way to do that is to repartition and reformat.

---

### Post by poofyhairguy on 2005-06-13
[QUOTE=wylfing]...and the only foolproof way to do that is to repartition and reformat.[/QUOTE]

Life....tis a witch sometimes.

---

### Post by zaxer on 2005-06-14
Can anyone explain what are the "technical" differences between a FAT32 partition and a NTFS one?

Not  you just can read and write here and only read here but  technical issues.


Thanks.

---

### Post by bored2k on 2005-06-14
[QUOTE=zaxer]Can anyone explain what are the "technical" differences between a FAT32 partition and a NTFS one?

Not  you just can read and write here and only read here but  technical issues.


Thanks.[/QUOTE]
Here you go. Make sure you clic on the two links below.
>  All three of the file systems (FAT16, FAT32 and NTFS) work like this. So what is the difference between FAT16 and 32? The major difference lies in how much space each file system can handle and how efficiently the file system does it. 
>    1.      NTFS is the best file system for large drives. Unlike FAT and FAT32, performance with NTFS isn't corrupted as drive size increases.
   2.      One of the major security features in NTFS is encryption or, in other words, the process of disguising a message or data in such a way as to hide its substance. <-- What this means is: in NTFS, Windows users can't read the other person's files unless they have permission. In FAT, there is no such barrier.
   3.      Another feature in NTFS is disk quotas. It gives you the ability to monitor and control the amount of disk space used by each user.
   4.      Using NTFS, you can keep access control on files and folders and support limited accounts. In FAT and FAT32, all files and folders are accessible by all users no matter what their account type is.
   5.      Domains can be used to tweak security options while keeping administration simple.
   6.      Compression available in NTFS enables you to compress files, folders, or whole drives when you're running out of disk space.
   7.      Removable media (such as tapes) are made more accessible through the Remote Storage feature.
   8.      Recovery logging helps you restore information quickly if power failures or other system problems occur. 


> FAT32 Has Better Performance and is More Efficient Than NTFS

This is completely untrue. NTFS is much more efficient than FAT32. Larger disks that are formatted FAT32 require far bigger File Tables. Larger file tables take longer to read. It is this for reason that XP will not allow you to create a FAT32 volume greater than 32GB in size.

XP Does Not Support FAT32 Drives Larger than 32GB

This is completely untrue. It does not follow that XP does not support FAT32 drives greater than 32GB just because it will not allow you to create a FAT32 volume greater than 32GB. If a disk is preformatted with FAT32, right up to the theoretical limit for FAT32 disks, XP will support it.

Windows 98 Cannot Read NTFS

This is only true insofar as Windows 98 cannot natively read NTFS disks. If you need to access a NTFS partition via Windows 98, you accomplish this with a third-party driver. Sysinternals offer a free, read-only driver that will allow Windows 98 to read a NTFS partition. If you need full read/write access, you can purchase the full version here .

NTFS Does Not Fragment 

This is completely untrue. File fragmentation is a fact of life, irrespective of the underlying file system. Files increase and decrease in size with use, or are created, deleted and recreated over and over. Operating Systems attempt to keep parts of files in their place as new clusters are added as and when they are needed. The allocation of additional clusters cannot be guaranteed to follow on sequentially from where the file currently resides and are almost always allocated from a completely different location on the disk. It is this allocation process that causes fragmentation.

If it were true that NTFS does not fragment, why is Windows XP shipped with a defragmentation tool?

DOS FDISK Does Not Support NTFS or FDISK Can Format NTFS Partitions

Uninformed rumours and unfounded statements about Windows 98 or DOS 6 FDISK make up one of the fishiest smelling red herrings about NTFS. The fact of the matter is, FDISK does not format any kind of partition. FDISK is a rudimentary partition manager. Furthermore, FDISK can work with NTFS partitions but it cannot delete NTFS partitions that are logical drives on extended partitions. Read the Formatting / Partitioning Hard Disks and Installing XP article on this site for more detail.

There are Very Few Recovery Tools for NTFS

This is completely untrue. Not only does Windows XP ship with some very extensive system recovery and protection  tools, it includes an impressive range of disaster recovery tools, far beyond what earlier versions of Windows ever provided. Plus there are a great munber of third-party tools available, a lot of them free, to supplement those that come with XP.

Windows XP provides advanced disk and maintenance tools you can use to prevent problems from occurring. Some of the most useful tools are discussed in the Dealing with Data Corruption article on this site. The disk-related tools allow you to view disk information and correct a problem before it becomes a serious issue.
[http://windows.about.com/od/filesfoldersdisks/l/aa001231a.htm](http://windows.about.com/od/filesfoldersdisks/l/aa001231a.htm)
[http://windows.about.com/od/filesfoldersdisks/l/aa001231b.htm](http://windows.about.com/od/filesfoldersdisks/l/aa001231b.htm)

---

