---
title: "Creating a shared partition for Ubuntu/Vista"
date: 2008-01-24
forum: Absolute Beginner Talk
---

### Post by Theros123 on 2008-01-24
Okay,

I've got a 160 gig harddrive on my laptop.  I've done a clean install of vista and Ubuntu.  So Vista has 20 gigs and ubuntu has 30.  The rest I planned to make into a NTFS shared partition that both can read and write off of.  The problem is that now that I have both Vista and ubuntu working, neither detected that partition automatically and so I changed it to a FAT32 partition to try to see if either one would pick it up.  Obviously neither did, and so I'm going to rechange it back to NTFS, and try that mount command in Ubuntu to see if it can read it.  However, how can I get vista to read that partition?

Thanks,
Eric Huang

---

### Post by LowSky on 2008-01-24
create the partition in Vista using disk management, and Ubuntu should automatically see it. At least my install does...?

---

### Post by kshane on 2008-01-24
> **Theros123 said:**
> Okay,

I've got a 160 gig harddrive on my laptop.  I've done a clean install of vista and Ubuntu.  So Vista has 20 gigs and ubuntu has 30.  The rest I planned to make into a NTFS shared partition that both can read and write off of.  The problem is that now that I have both Vista and ubuntu working, neither detected that partition automatically and so I changed it to a FAT32 partition to try to see if either one would pick it up.  Obviously neither did, and so I'm going to rechange it back to NTFS, and try that mount command in Ubuntu to see if it can read it.  However, how can I get vista to read that partition?

Thanks,
Eric Huang

A fat32 partition should work fine for both Windows and Linux.  I avoid all Windows based formats, otherwise.  Keeps my machine safer.

Kevin

---

### Post by monte48lowes on 2008-01-24
I recommend against using FAT32 since it is not a journaling file system. NTFS would be the recommend format using Vista. Although there have been many issues with windows not cleanly unmounting NTFS partitions. When this happens linux refuses to mount them (which is a good thing) until they are mounted and cleanly unmounted in windows. 

Additionally, ext3 can be used in windows using a driver available here:

[http://www.fs-driver.org/]("http://www.fs-driver.org/")

Mike

---

### Post by HermanAB on 2008-01-24
Hmm, rather don't use VFAT if you can help it.  It is not a robust file system and can lose data.  It is also very inefficient on large disks.  NTFS is robust and Linux has a driver for it called ntfs-3g.  The latest Linux versions including Ubuntu has this by default, so NTFS access from Linux is not a problem anymore.

Cheers,

Herman

---

### Post by Theros123 on 2008-01-24
Okay, almost done creating the new partition from Vista...geez, the built-in one is so slow compared to Gparted.  

Anyway, I'm wondering would it be possible that I can install applications (such as Word, or even games (the ones that work with Wine), into the shared partition and start them from Wine from ubuntu?  Do I need install Wine into that shared partition or not?  And can Vista start those applications from the shared partition as well?

---

### Post by monte48lowes on 2008-01-30
I understand what you are wanting to do. I think it's possible to do in some manner or another if the program does not need to write settings to the registry in order to function. The registry in wine would not be able to use the registry used by Vista. Therefore the settings would not transfer over. 

Something like a portable application designed (or modified) to run from a USB thumb drive could work. Installing that on the common drive and running it using wine in ubuntu and normally in vista.

It really depends on the program you are trying to use.

Mike

---

