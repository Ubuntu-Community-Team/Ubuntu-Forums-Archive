---
title: "Which MAXIMUM size for FAT32 is adviced to use for making partitions on a 160GB ?"
date: 2005-11-11
forum: Absolute Beginner Talk
---

### Post by patrick295767 on 2005-11-11
(wihtout data loss and used by linux)

---

### Post by Kyral on 2005-11-11
Max size? Like cluster size? I had a FAT32 partition on my entire 160 GB for a while and I just used the default. Just make sure you specify FAT32 with the command, which looks like this

```
sudo mkfs.vfat -F 32 <device>
```

---

### Post by blastus on 2005-11-11
The maximum FAT32 partition size possible is very large. However, with Windows XP, the maximum FAT32 partition size you can create is 32Gb. However, OEMs have tools that can create FAT32 partitions larger than 32Gb. I'm not sure if QTParted, GParted, or the Ubuntu installer partition manager allows you to create FAT32 partitions larger than 32Gb. Microsoft constrained FAT32 to 32Gb because the cluster size jumps from 16K to 32K right past the 32Gb boundary making the file system very inefficient.

---

### Post by Kyral on 2005-11-11
I *know* that mkfs.vfat can make a 160 GB FAT32 partition because I've done it

---

### Post by blastus on 2005-11-11
I wouldn't advise using FAT32 for anything other than temporarily sharing data between Windows and Linux. FAT32 is not a journaled file system and shouldn't be used for storing anything important. If you are using Windows use NTFS, if you are using Linux use ext3, and if you want to temporarily share data between the two use FAT32.

---

### Post by patrick295767 on 2005-11-11
[QUOTE=Kyral]I *know* that mkfs.vfat can make a 160 GB FAT32 partition because I've done it[/QUOTE]
  
AAhhhhh kyral, so then 
I guess I can make my fully 160Gb harddisk in one single FAT32 partition !!!
Actually, the purpose would be to be possible to read my external disk from a windows NT 2000 
  
I guess a windows98 wouldnt be capable of reading it
but a windows NT or XP coudl do so ! I guess. 
Let 's think a bit : the installation cd of windows NT 2000 is proposing you to format ur harddisk either in ntfs or fat32 before installing the system  ==========> that would means that FAT32 of a single partition of 160 gb could be readable with a windows NT 2000 ! !
  
Am I right ??
  
Someone has additional information ?
   
Thnak you very much guys !!
  
Patrick

---

### Post by Kyral on 2005-11-11
XP should be able to. I don't know the inner workings of XP

---

### Post by poptones on 2005-11-11
You can use linux to make a 160GB fat32 partition - just fdisk and mkfs and blammo.

A 160GB fat32 partition is a seriously bad idea. You WILL eventually lose data on a fat32 partition, and 160GB is a lot to endanger. Of course, it won't be as much to endanger if you have small files, since even the smallest will occupy a whopping 128K at that size...

---

### Post by xequence on 2005-11-11
If you shouldent have 160 GB FAT32 partitions, what do you do if you want linux and windows to be able to read and write?

Windows can only read ext3, Linux can only read NTFS.

---

