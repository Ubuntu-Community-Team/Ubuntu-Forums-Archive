---
title: "Common file system for Ubuntu, OS X, Windows?"
date: 2008-10-04
forum: Apple Hardware Users
---

### Post by CaptSkinny on 2008-10-04
The short and sweet version: I just built a new workstation that I'm planning to use with Ubuntu, Mac OS X, and Windows Vista in a multi-boot configuration. If at all feasible, I'd like to have a single data partition that I can use from all three operating systems. Can anyone make file system recommendations or provide instructive/constructive discussion? I plan to divide the single RAID 5 volume as follows: ~100 GB to Ubuntu, ~100 GB to Mac OS X, ~100 GB to Windows Vista, and ~1.8 TB to data.

The details:

I'm a long time Windows user who has decided to make the switch to Ubuntu (in large part to avoid Vista and still take advantage of all 8 GB of RAM in the system). I still have to use some Windows applications on a regular basis (e.g. AutoCAD, ESRI ArcGIS), so I can't completely abolish the OS. I also have a Macbook I have to use, and if I can put OS X on my new workstation, that's one less laptop cluttering up my workspace (and one less place to look for data).

Because I've invested in a RAID 5 array, I would very much like to consolidate the majority of my data on it (and in one partition, so it's easier to find and easier to back up).

Initially I was hoping to format my data partition as ext3. I've read that ext3 volumes can be mounted read/write in both Windows and OS X (as ext2, it seems), but I don't have a good sense of whether I should trust it as a solid solution. I know that Mac HFS+ volumes can be mounted in Windows with third-party commercial software, and I would be surprised if there was no port to Linux. But in any case, it seems I have to give up journaling features to use either of these file systems in non-native operating systems.

I instinctively don't trust read/write NTFS volumes as a permanent fixture in Linux, and I wouldn't dare use FAT32 on a 1.8 TB partition.

Thank you for any commentary - it's much appreciated.

Possibly Relevant System Specs:

Intel Core2 Duo E8500 CPU
8 GB RAM
3ware 9650SE Hardware RAID Controller, 256 MB Cache
4 x 750 GB Hard Disks in Single RAID 5 Array
System is powered by a UPS

---

### Post by cyberdork33 on 2008-10-04
> **CaptSkinny said:**
>  I also have a Macbook I have to use, and if I can put OS X on my new workstation, that's one less laptop cluttering up my workspace (and one less place to look for data). please do not discuss OS X on non-Apple hardware here.

> **CaptSkinny said:**
> Initially I was hoping to format my data partition as ext3. I've read that ext3 volumes can be mounted read/write in both Windows and OS X (as ext2, it seems), but I don't have a good sense of whether I should trust it as a solid solution. I know that Mac HFS+ volumes can be mounted in Windows with third-party commercial software, and I would be surprised if there was no port to Linux. But in any case, it seems I have to give up journaling features to use either of these file systems in non-native operating systems.

I instinctively don't trust read/write NTFS volumes as a permanent fixture in Linux, and I wouldn't dare use FAT32 on a 1.8 TB partition.As you have obviously already read, FAT32 is the most compatible filesystem between them all, with NTFS in a close second. There is nothing else worth mentioning really other than hfs+ which has poor support under windows and linux, and ext2/3 which has poor support in OS X.

---

### Post by annatar on 2008-10-04
I would recommend NTFS over FAT32 since...


[LIST=1]
[*]FAT32 has a number of limitations - the most obvious one being *unable to store files over 4GB.*
[/LIST]
       2. Ntfs-3g should be stable enough for everyday use

You will need some tinkering to get NTFS writing to work under Mac OS X though (google for 'MacFUSE'+'ntfs-3g')...if you can get OS X up on your machine

---

### Post by CaptSkinny on 2008-10-04
> **cyberdork33 said:**
> please do not discuss OS X on non-Apple hardware here.

I apologize if I'm not quite on topic - I saw the Apple Users category and though it would allow me to make sure at least two of my subjects were on topic: Ubuntu and OS X. But thanks for letting me know what's expected here.



> **annatar said:**
> Ntfs-3g should be stable enough for everyday use; You will need some tinkering to get NTFS writing to work under Mac OS X though

Thanks for the advice. I'll have to dig deeper into Ntfs-3g.

---

### Post by cyberdork33 on 2008-10-05
> **CaptSkinny said:**
> I apologize if I'm not quite on topic - I saw the Apple Users category and though it would allow me to make sure at least two of my subjects were on topic: Ubuntu and OS X. But thanks for letting me know what's expected here.
It is not just an Apple Users board topic limitation, it is an ubuntuforums rule... Just cautioning you :)

---

### Post by FinalJenemba on 2008-10-05
NTFS is your best option I think.  Iv been running NTFS on my storage drive for almost 2 years now with no problems/reformats.  Iv never had any problems using it with ubuntu either.

---

