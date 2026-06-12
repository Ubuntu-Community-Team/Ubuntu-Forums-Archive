---
title: "Error Making Filesystem"
date: 2008-03-12
forum: Absolute Beginner Talk
---

### Post by oxsyn on 2008-03-12
I'm not experienced with the mkfs command.  However, here's the relevant information:

> f4rr4r@Hawking:~$ sudo fdisk -l
[sudo] password for f4rr4r:

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
/dev/hdb1               1      155061    78150743+   5  Extended
f4rr4r@Hawking:~$

> f4rr4r@Hawking:~$ sudo mkfs.ext2 /dev/hdb1
[sudo] password for f4rr4r:
mke2fs 1.40.2 (12-Jul-2007)
mkfs.ext2: inode_size (128) * inodes_count (0) too big for a
        filesystem with 0 blocks, specify higher inode_ratio (-i)
        or lower inode count (-N).

f4rr4r@Hawking:~$

I'm not even sure what this error message means.  Please help?

---

### Post by PeterJS on 2008-03-12
You can not directly format hdb1, because it's an extended partition that contains no logical partitions. You can recreate hdb1 as a standard partition and then format that, or you create a logical partition inside of hdb1 and format the logical partition.

---

### Post by oxsyn on 2008-03-12
> **PeterJS said:**
> You can not directly format hdb1, because it's an extended partition that contains no logical partitions. You can recreate hdb1 as a standard partition and then format that, or you create a logical partition inside of hdb1 and format the logical partition.

When I created the partition hdb1 on hdb, I used fdisk and created it as an extended partition.  In doing this, does fdisk automatically create the file system (I.E. is mkfs.ext2 unnecessary?)  If so, am I ready to write to it right now?

---

### Post by Arkenzor on 2008-03-12
Extended partitions aren't partitions you can create a file system on. They're only containers for "normal" (logical) partitions (the partition table format for standard PCs originally only allows four partitions. Extended partitions are there to get around this: you create an extended partition in one of the four "slots", then fill it with as many logical partitions as you want).

So you'll need to use fdisk again in order to add logical partitions inside of your extended partition. You'll the be able to create a filesystem on them.

---

### Post by oxsyn on 2008-03-12
> **Arkenzor said:**
> Extended partitions aren't partitions you can create a file system on. They're only containers for "normal" (logical) partitions (the partition table format for standard PCs originally only allows four partitions. Extended partitions are there to get around this: you create an extended partition in one of the four "slots", then fill it with as many logical partitions as you want).

So you'll need to use fdisk again in order to add logical partitions inside of your extended partition. You'll the be able to create a filesystem on them.

Zomg, thank you ... that was exactly what I needed to know. :)  Very, very much appreciated.

---

### Post by oxsyn on 2008-03-12
After I got it runing, I mounted it to test it out:
sudo mkdir /library
sudo mount /dev/hdb1 /library

That's not where I really want it though.  So I tried to unmount it:

> f4rr4r@Hawking:/library$ umount /library
umount: /library is not in the fstab (and you are not root)
f4rr4r@Hawking:/library$ sudo umount /library
umount: /library: device is busy
umount: /library: device is busy
f4rr4r@Hawking:/library$


Any idea what I need to do to unmount it?  I'm going to put files on it that I want to be served by apache, so I'm going to mount it to /var/www/library ..

---

### Post by PeterJS on 2008-03-12
Like the error says, the device is busy. Is there a graphical file browser pointed at it? Is trackerd, or updatedb indexing it? Is a file from that parititon open? I don't think being in a shell within a directory of the mounted parition should be enough to make it busy, but you might try cd to another directory before trying to unmount it. If all else fails you can open up the gnome system monitor and see if there are any files from that paritioning being help open by something unexpected.

---

### Post by oxsyn on 2008-03-12
> **PeterJS said:**
> but you might try cd to another directory before trying to unmount it
That was exactly what I needed to do, thanks!

---

