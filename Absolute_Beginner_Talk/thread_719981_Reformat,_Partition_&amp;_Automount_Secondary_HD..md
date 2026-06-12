---
title: "Reformat, Partition &amp; Automount Secondary HD."
date: 2008-03-09
forum: Absolute Beginner Talk
---

### Post by oxsyn on 2008-03-09
As shown here, I've got a secondary HD installed in my server:

> f4rr4r@Hawking:~$ sudo fdisk -l

Disk /dev/hda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0a990a99

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       18985   152496981   83  Linux
/dev/hda2           18986       19457     3791340    5  Extended
/dev/hda5           18986       19457     3791308+  82  Linux swap / Solaris

Disk /dev/hdb: 80.0 GB, 80026361856 bytes
16 heads, 63 sectors/track, 155061 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes
Disk identifier: 0x000be3b0

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               3      155059    78148608    7  HPFS/NTFS
f4rr4r@Hawking:~$

I want to delete the hdb1 NTFS partition, reformat the entire drive, create an extended partition (that's what I should be using for a fileserver, right?) and have it automount.  I've played with fdisk, but do not remember the correct commands.

I assumed i would start out like this:

> f4rr4r@Hawking:~$ sudo fdisk hdb

Unable to open hdb
f4rr4r@Hawking:~$


but obviously, that's not right.  Help, please?  Thanks!

---

### Post by walsh416 on 2008-03-09
Assuming that you have Ubuntu installed, go to add/remove programs, download G-Parted, open it and it should be somewhat obvious from there.  If not, feel free to PM  me.  Hope I helped.

---

### Post by oxsyn on 2008-03-09
> **walsh416 said:**
> Assuming that you have Ubuntu installed, go to add/remove programs, download G-Parted, open it and it should be somewhat obvious from there.  If not, feel free to PM  me.  Hope I helped.

It's a ubuntu server installation that I'm sshing into.  I don't have access to gnome, so therefore I don't have access to run GUI programs ... so I believe it's gotta be done via fdisk :)

---

### Post by oxsyn on 2008-03-09
I just figured out the first part, I was needed to specify /dev/hdb instead of just hdb.
I now have a clean extended linux partition on hdb as hdb1.

I believe the next step is to create the filesystem.  I believe for this, I should be using either ext2 or ext3.  I'm not sure what the differences are, or the syntax for creating it/formatting it.  Any suggestions?

---

### Post by oxsyn on 2008-03-09
I found out that the primary difference between ext2 and ext3 is journaling.  Since I have mirrored the data on this server to another disk (only about 10g or so) and since I'm mainly just trying to learn to run my own server, I decided that journaling is not important right now and I'll stick with ext2.

So, I attempted to make an ext2 file system on the hdb1 partition:

> f4rr4r@Hawking:/etc/apache2$ sudo mkfs.ext2 /dev/hdb1
mke2fs 1.40.2 (12-Jul-2007)
mkfs.ext2: inode_size (128) * inodes_count (0) too big for a
        filesystem with 0 blocks, specify higher inode_ratio (-i)
        or lower inode count (-N).

f4rr4r@Hawking:/etc/apache2$


I have no idea with this error message means.  As far as I know, inodes are used when creating softlinks to files in a filesystem, right?  Why is this important when creating the filesystem and how to I avoid this error message?

Also, once I've created the filesystem, I believe the files will be mounted to /dev/hdb1 ... right?  If I wanted to mount them to some place more convenient, is there a convention I should follow?  Or would mounting them to some place like /library be acceptable (or would an experienced sysadmin scream at me?)

---

### Post by iris-n on 2008-03-09
As for the error message, i'm sorry but i can't help you, addicted to the gparted.

The standard mountpoint is /media/disk, or /media/sda*

Actually it's more polite to create a folder, and edit your /etc/fstab to tell it to use that as mount point. Personally i use /files, but i'm not aware of any convention.

---

