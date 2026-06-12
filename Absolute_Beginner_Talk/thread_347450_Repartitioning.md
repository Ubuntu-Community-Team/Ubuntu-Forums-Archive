---
title: "Repartitioning"
date: 2007-01-27
forum: Absolute Beginner Talk
---

### Post by calvinthomas on 2007-01-27
Hi, I'm wondering if the following is possible, a fairly long time ago I installed ubuntu and partitioned my harddisk 50/50 with Windows, however after installing everything I need on Ubuntu I have only used 36% of the space I gave to it, however on Windows (where I play games, have music etc) I have had to delete things because it is full, is it possible to repartition my ubuntu partition to something I can use in windows? Ideally perhapsto FAT32 then I could use it in both?

Calv

---

### Post by Sef on 2007-01-27
> is it possible to repartition my ubuntu partition to something I can use in windows? Ideally perhapsto FAT32 then I could use it in both?

Not with FAT32.  Both Windows and Linux will read and write to ext2 and ext3.   What file system did you use?

---

### Post by aktiwers on 2007-01-27
I can read/write to fat32 from Linux?
Works fine for me..

---

### Post by tonyr1988 on 2007-01-27
Yes, you can create a "shared" partition that will have music, documents, pictures, videos, etc that both operating systems can access.

Fat32 is going to have the best support for both (but with a few restrictions, like file size limit)
Ext2/3 is probably your second-best bet - since it's open-source, there are some Windows drivers for it
NTFS is possible, but the drivers are still beta (AFAIK)

---

### Post by calvinthomas on 2007-01-29
So how would I go about doing this, is it possible then for me to not repartition at all but allow my linux partition to be seen in windows? If so, how would I go about this, I'm using ubuntus standard file system (on Edgy)

Calv

---

### Post by mozetti on 2007-01-29
There is an Ext2 driver for Windows -- search for that on here. Once you install it in Windows, you'll be able to see/access your Ext2 Linux partition(s) from Windows.

---

### Post by housam on 2007-01-29
Install the following driver to read/write to ext2/ext3 from windows

[http://www.fs-driver.org/]("http://www.fs-driver.org/")

---

### Post by calvinthomas on 2007-02-02
Thankyou, that was most helpful, however I had to use the ext2fsd version because I'm using windows xp 64-bit edition.

Calv

---

