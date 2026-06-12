---
title: "How to set a mountpoint for external media"
date: 2007-08-27
forum: Absolute Beginner Talk
---

### Post by adempewolff on 2007-08-27
Hey I have all my files stored on an external hardrive and would like a static address for them so programs can access them.  As is Ubuntu automatically mounts them to /media/[disc, disc-1, disc-2, disc3] depending on the order it decideds to mount them and I just have to umount and remount until it mounts the partition my files are on to the right mountpoint.  Is there a way I can make it recognize this piece of external media and always mount it to the same mountpoint of my choosing?  Thanks.

---

### Post by bogolisk on 2007-08-27
> **adempewolff said:**
> Hey I have all my files stored on an external hardrive and would like a static address for them so programs can access them.  As is Ubuntu automatically mounts them to /media/[disc, disc-1, disc-2, disc3] depending on the order it decideds to mount them and I just have to umount and remount until it mounts the partition my files are on to the right mountpoint.  Is there a way I can make it recognize this piece of external media and always mount it to the same mountpoint of my choosing?  Thanks.

if your partitions on the external disc has label then ubuntu feisty will use that label as the mount point. I don't remember how it works  with older version of ubuntu (edgy, dapper, ...). E.g: my partition on the external disc was labeled BOGUS_DATA, upon connecting the on usb, feisty will mount the partition on /media/BOGUS_DATA.Thus, if you used feisty, just make sure your partitions on the external disc have label.

---

### Post by Phurious on 2007-08-27
I just learned a way to mount my drives to overcome a different problem, but it should serve your purposes.  First of all, what type of file system is on your USB drive?  NTFS?  FAT32? EXT3?

In terminal I ran:
```
blkid
/dev/sda1: UUID="b2b9d63e-f8df-4f05-8712-57aad71e76ed" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdc1: UUID="ccb0ced2-a212-4afb-a652-252e576e2424" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdb1: UUID="9e6ecdf2-843f-4337-af1c-46939db7f6f8" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdb5: TYPE="swap"
```

Which returned the above UUID's for each of my drives.  I then edited my FSTAB file to mount the above ID's to a specific folder.  Below is a snippet of my FSTAB file.
```
UUID=ccb0ced2-a212-4afb-a652-252e576e2424 /mnt/RAID ext3 defaults,noatime,nodiratime,data=writeback 0 0
UUID=b2b9d63e-f8df-4f05-8712-57aad71e76ed /mnt/DATA ext3 defaults,noatime,nodiratime,data=writeback 0 0
```

What file system is on your USB drive will determine what command you must use when you edit you FSTAB file.  Also, the points you wish to mount the drives to must already exist - if not the mount command will fail.  I myself had to create the folders "RAID" and "DATA" in the /mnt directory in order to mount my drives using the above entries in my FSTAB file.

---

