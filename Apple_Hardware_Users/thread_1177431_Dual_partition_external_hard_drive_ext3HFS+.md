---
title: "Dual partition external hard drive ext3/HFS+?"
date: 2009-06-03
forum: Apple Hardware Users
---

### Post by Dingbats on 2009-06-03
I just got a 1TB external hard drive that I want to use for making backups both from Ubuntu (where I use ext3) and Mac OS X (HFS+).  I don't *think* it should be a problem, but can I just split it in half and use one ext3 partition from Ubuntu and one HFS+ partition from OS X?

---

### Post by Dingbats on 2009-06-03
Anyone?

---

### Post by JGreenidge on 2009-06-03
> **Dingbats said:**
> I just got a 1TB external hard drive that I want to use for making backups both from Ubuntu (where I use ext3) and Mac OS X (HFS+).  I don't *think* it should be a problem, but can I just split it in half and use one ext3 partition from Ubuntu and one HFS+ partition from OS X?

I'm hoping for an answer too because I'd like to backup my Ubuntu 9.04 partition on a HD's spare UNIX patition (or somehow reformat it into one that'll take it without altering other Mac ones) but I'm lost as to what backup software to use since Retrospect doesn't even see Ubuntu partitions.

Geekless Jim

---

### Post by MikeTheC on 2009-06-04
What I would suggest is looking into going with MacFuse and NTFS support, and then just formatting the drive as NTFS since NTFS-3G read/write is also supported under Linux.

The reason for that instead of, say, FAT32, is max file size limitations. Now, if you know FOR A FACT that you'll never ever exceed 2.1GB (or whatever the exact size is) then you could go with FAT32.

I have no idea whether any backup utility will support any partition mounted under Mac OS X that doesn't necessarily use the native HFS+ file system. You'll just have to experiment.

---

### Post by tiresia on 2009-06-04
> **Dingbats said:**
> I just got a 1TB external hard drive that I want to use for making backups both from Ubuntu (where I use ext3) and Mac OS X (HFS+).  I don't *think* it should be a problem, but can I just split it in half and use one ext3 partition from Ubuntu and one HFS+ partition from OS X?

Yes, you can do it without any problems. For Ubuntu you can use ext3, but also ext4 (if your kernel supports it) or reiserfs.
Ubuntu can read also HFS+ Journaled, but it can't write on it. If you want that Ubuntu can also write it, you should disable Journaling (in MacOSX, you can't do it in Ubuntu)
If you want just two 'separated worlds' just ignore it, and format the partition for MacOSX backup as HFS+ Journaled (in the Apple Disk Utility)

As said in the last post both Systems can read/write on FAT32 with the file limitation of 4GB for one file.

---

### Post by maflynn on 2009-06-04
I have an external drive setup just the way you describe it and found no problems.  I have 50% of the drive formatted for HFS+ and another 50% formatted to ext3.

I used gparted to move, shrink the HFS+ partition and created the ext3 without any problems. Now both systems can backup to my external drive.

---

### Post by Dingbats on 2009-06-04
Great, thanks guys!  I'll just split it up :)

---

### Post by cyberdork33 on 2009-06-04
yep. format the drive with disk utility with two partitions, make the first HFS+ and the second "free space". Then in Ubuntu create a linux partition (whatever filesystem you want) with gparted.

---

### Post by GeneralSunTzu on 2009-07-23
> **cyberdork33 said:**
> yep. format the drive with disk utility with two partitions, make the first HFS+ and the second "free space". Then in Ubuntu create a linux partition (whatever filesystem you want) with gparted.

Thank you cyberdork, and then backup with what? 
sbackup seems unable to back to an external FW drive.
Should one use any other recommended program?
[I hope I am not hijacking this thread, hopefully am just following it up]

Thank you.

---

