---
title: "Ntfs"
date: 2006-08-15
forum: Absolute Beginner Talk
---

### Post by jesus of suburbia on 2006-08-15
does linux, er support NTFS format, thanks dudes

---

### Post by jesus of suburbia on 2006-08-15
um. help

---

### Post by Klaidas on 2006-08-15
Linux can read from NTFS drives, but writing to them is still experimental, if that;s what you asked :)

---

### Post by goatflyer on 2006-08-15
Linux can safely read.  It CAN also write, but they don't recommend it yet.  You can mount your NTFS volumes as read-only, and use a FAT32 partition to share data files between windows and linux.

---

### Post by jesus of suburbia on 2006-08-15
oh, but when i start up linux (installation) when i make up a partition will it  be in fat32 format, or do i have to use my windows diskpart to make a new fat32 partition before i use linux?

---

### Post by harakiri on 2006-08-15
There is a very well written How-to on this forum why donot you search for it.

Edit:[http://ubuntuforums.org/showthread.php?t=217009&highlight=ntfs-3g]("http://ubuntuforums.org/showthread.php?t=217009&highlight=ntfs-3g")

i didnot understand your question.. can u b more clear?

---

### Post by jesus of suburbia on 2006-08-15
can you please direct me to one of the how tos please harakiri

---

### Post by jesus of suburbia on 2006-08-15
thanks for the howqto, i said, when i am installing linux, does it make a fat32 partition, or do i have to use the microsoft disk  management to make one before i use linux?

---

### Post by gruffy-06 on 2006-08-15
It is illegal to gain write access to NFTS partitions under GNU/Linux, because Microsoft holds the patent of NTFS. See [http://en.opensuse.org/Restricted_Formats](http://en.opensuse.org/Restricted_Formats).

---

### Post by RRS on 2006-08-15
> **jesus of suburbia said:**
> thanks for the howqto, i said, when i am installing linux, does it make a fat32 partition, or do i have to use the microsoft disk  management to make one before i use linux?

If you select the "manually partition" option during the installation you'll be able to create a fat32 partition along with your new linux(ext3) partition while retaining your windows(ntfs) partition.

If you're using the desktop/live cd follow [this guide]("http://psychocats.net/ubuntu/installing.html"). For the alternate/text based cd use [this guide]("http://users.bigpond.net.au/hermanzone/index.htm").

A couple things;
If you create  a fat32 partition from windows there's a size limit (32g I think) that Linux doesn't have.
Though problems rarely occur, backup any important data before partitioning.
Do a full defrag of windows before partitioning.

Both the sites I linked to also have a lot of good info for setting things up after you install too.

---

