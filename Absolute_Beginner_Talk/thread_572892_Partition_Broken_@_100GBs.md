---
title: "Partition Broken @ 100GBs???"
date: 2007-10-10
forum: Absolute Beginner Talk
---

### Post by P3RH4PS on 2007-10-10
I created a Fat32 partition so that XP and Ubuntu can share the drive and I was copying files onto the partition and it said the drive was full.  But when I look in XP it says there's 100GB free.  Is this a common issue?

---

### Post by Frak on 2007-10-10
> **P3RH4PS said:**
> I created a Fat32 partition so that XP and Ubuntu can share the drive and I was copying files onto the partition and it said the drive was full.  But when I look in XP it says there's 100GB free.  Is this a common issue?
I wouldn't worry about it, but, to be safe. Put a file onto there, and see if XP can see it and read it, and vise-versa.

---

### Post by Sef on 2007-10-11
I would download [GParted]("http://gparted.sourceforge.net") and see what it says.

---

### Post by LowSky on 2007-10-11
how big was the file. FAT32 can only hadles file sizes smaller than 4GB

---

### Post by hyper_ch on 2007-10-11
Did you formate it with FAT32 upon instalaltion of WinXP?

If so, have a read here: [http://support.microsoft.com/kb/314463/en-us](http://support.microsoft.com/kb/314463/en-us)

> 
The maximum disk size is approximately 8 terabytes when you take into account the following variables: The maximum possible number of clusters on a FAT32 volume is 268,435,445, and there is a maximum of 32 KB per cluster, along with the space required for the file allocation table (FAT).


> 
You cannot format a volume larger than 32 gigabytes (GB) in size using the FAT32 file system during the Windows XP installation process. Windows XP can mount and support FAT32 volumes larger than 32 GB (subject to the other limits), but you cannot create a FAT32 volume larger than 32 GB by using the Format tool during Setup. If you need to format a volume that is larger than 32 GB, use the NTFS file system to format it. Another option is to start from a Microsoft Windows 98 or Microsoft Windows Millennium Edition (Me) Startup disk and use the Format tool included on the disk.


---

