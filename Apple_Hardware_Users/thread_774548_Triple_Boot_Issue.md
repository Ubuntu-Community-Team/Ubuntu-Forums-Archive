---
title: "Triple Boot Issue"
date: 2008-04-29
forum: Apple Hardware Users
---

### Post by TheFonze on 2008-04-29
I just installed Ubuntu 7.01 and XP on my Macbook Pro using this guide.

[http://macapper.com/forums/showthread.php?t=134](http://macapper.com/forums/showthread.php?t=134)

All went well and I can now triple boot without the dreaded missing hal.dll in XP (woo hoo!).

My problem is this.

I cannot mount my XP partition in OS X. I can see it in Ubuntu and XP runs OK. 

This is my configuration according to disutil in OS X.

/dev/disk0
   #:                       TYPE NAME                    SIZE       IDENTIFIER
   0:      GUID_partition_scheme                        *149.1 Gi   disk0
   1:                        EFI                         200.0 Mi   disk0s1
   2:                  Apple_HFS Macintosh HD            107.9 Gi   disk0s2
   3:       Microsoft Basic Data                         8.6 Gi     disk0s3
   4:         Microsoft Reserved                         32.2 Gi    disk0s4

 Partition 3 is my linux ext3 partition and partition 4 is my XP NTFS partition. Even though OS X see's them as Microsoft Basic Data and Microsoft Reserved partitions.

I really need to be able to access my NTFS drive from OS X.

Any help would be greatly appreciated.

Thank You

---

### Post by cyberdork33 on 2008-04-29
NTFS is not supported by default under OSX that I know of... you have to use MacFUSE.

---

### Post by TheFonze on 2008-04-30
I should be able to read NTFS by default but not write. I can't mount the partition at all

---

### Post by cyberdork33 on 2008-04-30
I think this is your issue:
[http://www.macosxhints.com/article.php?story=20080130022147512](http://www.macosxhints.com/article.php?story=20080130022147512)

---

