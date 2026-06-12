---
title: "Upper limit to # of files in a directory?"
date: 2007-06-28
forum: Absolute Beginner Talk
---

### Post by Cheese Sandwich on 2007-06-28
Is there an upper limit to the number of files in a directory (like 2^8, for example)?

-Thx

---

### Post by Tsen on 2007-06-28
It varies.  First off, depending on what file system your Linux install uses.  The default is ext3, but even within that filesystem, the maximum number of files varies.  From Wikipedia:
> The maximum number of inodes (and hence the maximum number of files and directories) is set when the file system is created. If V is the volume size in bytes, then the default number of inodes is given by V/2^13 (or the number of blocks, whichever is less), and the minimum by V/2^23. The default was deemed sufficient for most applications.

---

### Post by Cheese Sandwich on 2007-06-28
> **Tsen said:**
> It varies.  First off, depending on what file system your Linux install uses.  The default is ext3, but even within that filesystem, the maximum number of files varies.  From Wikipedia:

Holy cow - then for my main drive (mounted as type ext3):

237405788 1K blocks = 237405788000 B / 213 ~= 1.1 billion

No particular limit within a single directory, though? Just wondering, as I'm considering an application that could accumulate a large number of files in a single directory.

---

### Post by pmg on 2007-06-29
If you run "**df -i**" it will tell you the number of inodes for each mounted filesystem as well as how many are in use and how many are left free.  (Some filesystems create inodes on the fly, and so this doesn't always apply.  For example, reiserfs does this.)  That is the upper limit of the number of files (and directories) that can be created in that **filesystem**.  In some cases, larger files can use multiple inodes, but unless you have a large bytes-per-inode ratio you'll run out of disk space before you run out of inodes.

In general, as the number of files in a directory increases, accesses and espically modifications to it become less effiicient.  At what point that becomes noticeable depends on the filesystem.  I generally try to avoid more then a couple thousand files in a directory, largely because it starts to get to be hard to keep things organized.  I think I've read that ext3 can handle the whole fileystem filled up in one flat directory, if you're not worried about performance.

---

### Post by Cheese Sandwich on 2007-06-29
Thanks to both for the info. 8)

---

