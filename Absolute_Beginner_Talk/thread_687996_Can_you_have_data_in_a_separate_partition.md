---
title: "Can you have data in a separate partition?"
date: 2008-02-04
forum: Absolute Beginner Talk
---

### Post by mojomike on 2008-02-04
Hi all.

I've set up my system to dual boot between Ubuntu 7.1 and MS Vista. I'm keeping vista because there are some programs I need for business that will only run on Windows. 

Anyway, I would like to avoid having data strewn about accross both partitions.  I'd like to set up a third partition for all of my data, which I would like to be accessible from both Vista and Ubuntu.  Is this possible?  How should the data partition be formatted?

Thanks for the advice!

,MPS

---

### Post by rudder on 2008-02-04
People do this all the time.  I believe the simplest way to do that would be to format the partition as FAT32.

---

### Post by Rocket2DMn on 2008-02-04
FAT32 is the easiest way, but you can also do NTFS which doesn't have the 4 GB file size limit.  For ntfs, you can use the ntfs-3g driver in linux to read/write to the partition (it comes installed with 7.10).
You could even just leave everything on the windows partition and access it from linux with ntfs-3g, so no new partitions are necessary.

---

### Post by bodhi.zazen on 2008-02-04
+1 FAT32

You can also use NTFS or EXT2/3. 

Linux can rw ntfs with the ntfs-3g driver and Vista can access EXT2/3 with the fs-driver :

_For access to ext2/3 from windows see_ : [http://www.fs-driver.org/](http://www.fs-driver.org/)
[indent]Vista: Install the fs-driver using the "Windows XP compatibility mode"[/indent]

---

### Post by mojomike on 2008-02-05
Great.  Thanks for all the help!

What is the difference between ext2 and ext3?

,MPS

---

### Post by jken146 on 2008-02-05
Ext3 is ext2 plus journalling.  Ext3 is backwards compatible with ext2 drivers, so the Windows drivers that read/write ext2 will work for ext3 as well.

I don't really see the point in using FAT32 when there is excellent NTFS support in Ubuntu now.

If you want to take advantage of file permissions in Linux, use a linux filesystem.  By the way, the ext2 Windows driver will ignore the permissions.

---

