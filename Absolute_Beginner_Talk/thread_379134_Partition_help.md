---
title: "Partition help"
date: 2007-03-08
forum: Absolute Beginner Talk
---

### Post by hrolfp on 2007-03-08
Hi,

I'm currently using a dell inspiron 6400 laptop and was interested in switching to ubuntu while still having windows on my disk.  I'm having a problem in that there's already 3 partitions on my disk. I can create the root partition, but I can't create the swap partition due to the 4 partition limit on the drive. 

Of the 3 partitions I currently have, one is the main windows ntfs partition, the second is a FAT dell utility partition, and the 3rd is a CP/M partition containing a ghost image backup. I'm not sure whether I should be deleting any of them, so I was wondering what to do. Any help would be appreciated.

---

### Post by Kateikyoushi on 2007-03-08
You can create an extended partition because / and swap can be logical partition as well.

---

### Post by hrolfp on 2007-03-08
Cool, thanks.

I'm having a second problem during the manual partition process. It's saying I have no root file system, but I have a / mountpoint defined. Here's a screenshot:

[http://img152.imageshack.us/my.php?image=screenshotmx6.png](http://img152.imageshack.us/my.php?image=screenshotmx6.png)

any help?

---

### Post by Bartender on 2007-03-08
Try going back and reformatting that partition again.  I got that same error message on a partition that hadn't been re-formatted.  Have read numerous other posts with same quirky problem that usually went away by re-formatting.  Try formatting it as ext3.

---

### Post by Kateikyoushi on 2007-03-08
I agree and most likely you won't use the dell partitions so set mount only for windows.

---

