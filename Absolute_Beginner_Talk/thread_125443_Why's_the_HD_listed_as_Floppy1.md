---
title: "Why's the HD listed as Floppy1?"
date: 2006-02-03
forum: Absolute Beginner Talk
---

### Post by keithbraafladt on 2006-02-03
- and I have a second partition on my HD listed as free space, is there a tool that can format it to make that available to Ubuntu?
Thanks

---

### Post by bscbrit on 2006-02-04
To format a partition for use look up the following at the commanline:

man mkfs

This 'makes a file system' - the format that you usually want for linux is ext2, ext3 or reiserfs.  Use vfat if you wish to share the partition with windows.

Be careful! If you format the wrong partition you will lose data.  To find out what partitions you have and what they are used for try

man fdisk
and
man df

---

