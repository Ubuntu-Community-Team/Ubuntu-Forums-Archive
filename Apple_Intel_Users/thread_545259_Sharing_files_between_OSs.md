---
title: "Sharing files between OSs"
date: 2007-09-07
forum: Apple Intel Users
---

### Post by r76 on 2007-09-07
Hi I'm interested in purchasing my first Apple, a new Macbook.  I'm going to run Windows XP with Boot Camp or rEFIt but want to also run OSX, and am interested in running Ubuntu too if it doesn't get too complicated.  I've read about a dozen guides to dual/triple-booting but one thing I don't get is which OS can read from the other filesystems?

I currently dual boot XP and Ubuntu.  XP is in an NTFS partition, Ubuntu ext3.  My external drive is ext3.  By running ext2 ifs in windows, and ntfs-3g in Ubuntu, all my files are available to me for read/write access whichever OS I boot into and wherever I left my files.

What solutions are available when I'm using HFS+?  Your experiences (positive or negative) are appreciated!

---

### Post by cyberdork33 on 2007-09-07
HFS+ is readable in linux. You can write to HFS+ as long as journaling is turned off.
This should help:
[http://ubuntuforums.org/showthread.php?t=509432](http://ubuntuforums.org/showthread.php?t=509432)

---

### Post by r76 on 2007-09-10
Thanks, that sounds good - although wouldn't journaling be better to be switched on?  Is there any way I can easily make another partition for data only that can be accessed by each OS.

And I have been reading about there is a new version of OSX expected in October, I know it will have boot camp pre-installed but has there been any hint it might also include the ntfs-3g driver or equivalent - that would make it worth waiting a few weeks I suppose.

---

