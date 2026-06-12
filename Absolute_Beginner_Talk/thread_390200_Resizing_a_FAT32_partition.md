---
title: "Resizing a FAT32 partition"
date: 2007-03-21
forum: Absolute Beginner Talk
---

### Post by slibuntu on 2007-03-21
I've been trying to resize my FAT32 formatted external harddrive to try out SUSE, but the install brings an error when i try and resize it. I've tried using gParted to create the partitions i need, but it gives me the same problem, whats going on??

---

### Post by euler_fan on 2007-03-21
A couple preliminary questions:

1) how many primary partitions do you have currently?

2) Can you post the text of the error?

3) Have you tried using the ubuntu live cd and gparted on that? I have successfully resized by own HD that way--with the drive unmounted.
3a) Was the drive mounted when you tried to re-partition?

4) What kind of HD do you have?

That should help some of the people on here who know more than I do diagnose things.

EDIT: From what I have read, external drives can be extra picky about things. I appeal to others for more detailed help. Is there a SUSE hacks book out there?

---

### Post by slibuntu on 2007-03-21
1) Just the one primary partition


2) Details on error;
GParted 0.2.5

Resize /dev/sdb1 from 298.09 GiB to 249.20 GiB    ( ERROR )
     	
check filesystem on /dev/sdb1 for errors and (if possible) fix them    ( SUCCES )
     	
dosfsck -a -w -v /dev/sdb1
     	
dosfsck 2.11 (12 Mar 2005)
dosfsck 2.11, 12 Mar 2005, FAT32, LFN
Checking we can access the last sector of the filesystem
No FSINFO sector
Not automatically creating it.
Boot sector contents:
System ID "MSWIN4.1"
Media byte 0xf8 (hard disk)
512 bytes per logical sector
32768 bytes per cluster
32 reserved sectors
First FAT starts at byte 16384 (sector 32)
2 FATs, 32 bit entries
39062016 bytes per FAT (= 76293 sectors)
Root directory start at cluster 2 (arbitrary size)
Data area starts at byte 78140416 (sector 152618)
9765385 data clusters (319992135680 bytes)
63 sectors/track, 255 heads
63 hidden sectors
625137282 sectors total
Reclaiming unconnected clusters.
/dev/sdb1: 5888 files, 945183/9765385 clusters
resize partition and filesystem using libparted    ( ERROR )
     	
File system is reporting the free space as 1701998624 clusters, not 8820202 clusters.
check filesystem on /dev/sdb1 for errors and (if possible) fix them    ( SUCCES )
     	
dosfsck -a -w -v /dev/sdb1
     	
dosfsck 2.11 (12 Mar 2005)
dosfsck 2.11, 12 Mar 2005, FAT32, LFN
Checking we can access the last sector of the filesystem
No FSINFO sector
Not automatically creating it.
Boot sector contents:
System ID "MSWIN4.1"
Media byte 0xf8 (hard disk)
512 bytes per logical sector
32768 bytes per cluster
32 reserved sectors
First FAT starts at byte 16384 (sector 32)
2 FATs, 32 bit entries
39062016 bytes per FAT (= 76293 sectors)
Root directory start at cluster 2 (arbitrary size)
Data area starts at byte 78140416 (sector 152618)
9765385 data clusters (319992135680 bytes)
63 sectors/track, 255 heads
63 hidden sectors
625137282 sectors total
Reclaiming unconnected clusters.
/dev/sdb1: 5888 files, 945183/9765385 clusters

========================================

3)I don't have a live cd handy unfortunatly but i was using the partition manger on the suse disk
Drive was unmounted

4) Its a 320gb usb hd

---

### Post by slibuntu on 2007-03-21
Bumpedy bump bump!

---

### Post by slibuntu on 2007-03-22
....noone?...  :-(

---

### Post by slibuntu on 2007-03-28
And the final bump.....

---

### Post by confused57 on 2007-03-28
If you haven't already, you might want to try the latest gparted live cd(30 mb download):
[http://gparted.sourceforge.net/screenshots.php](http://gparted.sourceforge.net/screenshots.php)

---

### Post by slibuntu on 2007-12-07
I had no luck with using the live cd, anyone got any idea why this isn't working for me?

---

