---
title: "Partitioning Scheme"
date: 2008-04-19
forum: Apple Intel Users
---

### Post by jakejackjacob on 2008-04-19
#:                       TYPE NAME                    SIZE       IDENTIFIER
   0:      GUID_partition_scheme    *232.9 Gi   disk0
   1:      EFI                                       200.0 Mi   disk0s1
   2:      Apple_HFS Mac OS               31.9 Gi    disk0s2
   3:      Linux Swap                             1.4 Gi     disk0s3


Ok. Here's what I've got. but when I try to resize my Apple HFS volume in diskutil (GUI) it gives me a "mediakit" error and I can't resize it. Also, it won't let me delete my linux swap partition.  I have 200g just sitting there, but I can't seem to format them for use.

<>< Jack

---

### Post by guj4_n3b3sk4 on 2008-04-19
Have you tried to resize it from booted OS X DVD? Insert install DVD, hold c while booting, and then go to diskutil and try to resize it.

---

### Post by bluefish86 on 2008-04-20
Have you tried booting an Ubuntu live CD and using the partition editor in the installer to delete your swap?  Maybe it's in the way of the expansion.

Also, I've heard of bad experiences trying to use diskutil to enlarge partitions.  If you have a free external hard disk, I might recommend something else.  Use Carbon Copy Cloner (Mac program, uncrippled donationware) to backup your HFS+ partition to the external.  When it's done, boot off the external hard drive.  Reformat the entire internal hard drive into the partitioning scheme you want using disk utility, and then use Carbon Copy Cloner to restore the backup onto the newly blanked disk (Carbon Copy Cloner is designed to make bootable copies of active partitions).

---

