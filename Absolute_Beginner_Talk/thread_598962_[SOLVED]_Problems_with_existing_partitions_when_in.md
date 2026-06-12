---
title: "[SOLVED] Problems with existing partitions when installing Ubuntu."
date: 2007-10-31
forum: Absolute Beginner Talk
---

### Post by gs110 on 2007-10-31
When I try to partition My drive for Ubuntu(7.10) in the installation, it gives me this message:

File system doesn't have expected sizes for Windows to like it. Cluster size is 2k (1k expected); number of clusters is 28034 (55960 expected); size of FATs is 110 sectors (219 expected).

Then when I go back to try and fix it, I get this message:

The test of the file system with type fat16 in partition #1 of SCSI1 (0,0,0) (sda) found uncorrected errors.
If you do not go back to the partitioning menu and correct these errors, the partition will be used as is.

The partition table that I tried to create looked like this:

Device         Type    Mount point   Format?   Size         Used
/dev/sda
  /dev/sda1   fat16  /media/sda1                57MB      33MB
  /dev/sda2   ntfs    /media/sda2                83922MB unknown
  /dev/sda5   ext3   /                                 159998MB unknown
  /dev/sda6   swap                                   1028MB   unknown
  /dev/sda3   fat32  /media/sda3                4984MB   4200MB
  unusable                                               8MB

Thanks for any help.

---

### Post by gs110 on 2007-11-01
I got some advice elsewhere:
[http://ubuntuforums.org/showthread.php?t=599287](http://ubuntuforums.org/showthread.php?t=599287)

---

