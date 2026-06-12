---
title: "Read/write to external hard drive?"
date: 2007-05-17
forum: Apple Intel Users
---

### Post by Seamyst on 2007-05-17
I have an external hard drive that is formatted for Mac (sorry, don't know the filesystem offhand), and it already has a bunch of data on it.  I can read from it just fine in Feisty, but I can't write to it.  Is there any way to be able to write to my external, without reformatting it and losing all the data?  (Or, reformatting it after copying my data over and burning it to several DVDs.)

I can, I guess, save files to be backed up to the shared partition (once I get that up and running), and then boot into Tiger and transfer the files that way.  It just seems like too many steps for a simple backup.

---

### Post by benanzo on 2007-05-17
If you were using the external disk in OS X it is probably formatted as HFS+.  have a look at this HowTo [http://ubuntuforums.org/showthread.php?t=392287](http://ubuntuforums.org/showthread.php?t=392287)  by Dirk.R.Gently for reading/write/resizing/reformatting HFS+ volumes under Ubuntu.

---

### Post by ronocdh on 2007-05-17
> **benanzo said:**
> If you were using the external disk in OS X it is probably formatted as HFS+.  have a look at this HowTo [http://ubuntuforums.org/showthread.php?t=392287](http://ubuntuforums.org/showthread.php?t=392287)  by Dirk.R.Gently for reading/write/resizing/reformatting HFS+ volumes under Ubuntu.
Dirk's guide looks pretty slick, and his advice is always stellar, but I just want to encourage you to use ext3 as it can be used on all three major OSes. In fact, I format all my external drives (not counting pen drives which are FAT32) to ext3 and then use installable filesystems to add compatibility to [OS X]("http://sourceforge.net/projects/ext2fsx/") and even [Win XP]("http://www.fs-driver.org/"). Both are extremely stable in my experience. I love it!

That said, much luck getting r/w with HFS+. Please post back with your results, maybe on Dirk's thread, if you use it.

---

