---
title: "Fat32 question"
date: 2006-11-10
forum: Absolute Beginner Talk
---

### Post by Grimesville89 on 2006-11-10
I am planning to install Ubuntu 6.10 this weekend and have a question concerning partitions.  I have decided on a XP/fat32/Ubu/swap setup.  Because I would like to store my files on the fat32 part to be able to access it from both Ubu and XP.  My question is how do I transfer all my files from My Docs, My Pics, and My Music on XP to the fat32 part?

Also, is there a good resource/book for the complete absolute newbie to linux?  

--GV89

---

### Post by hotbrainz on 2006-11-10
It would be a good idea to check this link by Aysiu:

[http://www.psychocats.net/ubuntu/]("http://www.psychocats.net/ubuntu/")

Welcome to Ubuntu

Cheers

---

### Post by Tamil on 2006-11-10
> **Grimesville89 said:**
> My question is how do I transfer all my files from My Docs, My Pics, and My Music on XP to the fat32 part?Right click on **My Documents** and select **Properties**. In **Target** type new location (fat32 partition) and click **Move...**

---

### Post by Carlos Santiago on 2006-11-10
It is easier than you think. The safter option, as you probably are more familiar with windows, is to prepare you hard drive in windows. 
I will assume that you have 3 partitions:
 1 - NTFS that will be your C: drive in windows
 2 - FAT32 that will be your D: drive 
 3 - Empty space that will be used by Ubuntu (at least of 4G + 2*RAM).

Before install Ubuntu, write down the sizes of your partitions.
I also advise you to have a backup copy of your most important files in both partitions. 

Start the installation, booting from Ubuntu CD.

Ubuntu Install CD will recognize your partitions, present its sizes and and format types. Check your notes.

Select the empty space and make a SWAP partition two times the amount of RAM you have (that is the size I usually select).

Select the remind of your HardDrive (at least 4GB) and make it as your root (/) partition and choose EXT3 filesystem (or format type as it is called in Windows)

The continue with installation untill the end.

You will see that Ubuntu will recognize your partitions, but the access to your NTFS will be read-only.

Both operating systems will read and write in your FAT32 partition, with no problem.

---

