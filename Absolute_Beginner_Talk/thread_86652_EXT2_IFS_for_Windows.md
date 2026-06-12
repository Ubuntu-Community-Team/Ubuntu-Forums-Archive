---
title: "EXT2 IFS for Windows"
date: 2005-11-06
forum: Absolute Beginner Talk
---

### Post by aum11 on 2005-11-06
This program looks like an easy way of accessing linux data from Windows.

Is this an alternative to creating a shared FAT32 partition?

Any comments, experiences with this program?  Is it well proven?

---

### Post by suRoot on 2005-11-06
I have used it before and can't say I had any problems with it.  However, my opinion would be to go with FAT32 if you're going to share data.  I'm always a little nervous about writing important data to disk with a third party extension under windows.  I know FAT works under both OS'es and that's good enough for me.

---

### Post by 23meg on 2005-11-06
Me too, I use that program to *read from* EXT3 only. When I need to transfer something to a Linux partition I just leave it on the NTFS partition and grab it from within Linux.

---

### Post by 23meg on 2005-11-06
Btw, there seems to be more than one program with the same name. I use and recommend [this one]("http://www.fs-driver.org/").

---

### Post by Freddie on 2005-11-06
I use it and it works fine, much better than a FAT 32 partition. Many people see it the same as writing to NTFS on Linux, but there is a difference, Ext 3 is open source and so it is easy to work out how to make a file system interface for it.
FAT 32 is not a good file system, because it does not allow files bigger than 4gb, and starts to crap out at around 32Gb, and pads files out so that they are multiples of 32k. Not good at all, so I use Ext2 IFS (for my 80gb Ext 3 partition) and have had no trouble with it.

---

### Post by aum11 on 2005-11-06
Thank You all for your excellent input.  Based on Your advice I installed IFS and have been using it happily....no probs.

I have used IFS to move all of my music and pictures from ntfs and fat32 partitions into an ext3 partition.  The fat32 is now empty and I will recycle that space into ext3.  The ntfs partition will be downsized.

For me, this is a much simpler approach.  I am nearly always running Linux so it makes sense to have as much data as possible in the linux partition.  Windows is only used for a very few applications.

---

### Post by psyguy92 on 2005-11-20
I have had success with this program ([www.fs-driver.org)](www.fs-driver.org)). but something bothers me a bit.

If my linux partitions have read/write access from windows, aren't my linux partitions as vulnerable as windows?  It would seem to me that a nice windows virus executed on XP could dest the linux partitions.  Even a 'nice' program could mess things up if it tried to write something strange, or delete things.

Does this seem accurate?

---

