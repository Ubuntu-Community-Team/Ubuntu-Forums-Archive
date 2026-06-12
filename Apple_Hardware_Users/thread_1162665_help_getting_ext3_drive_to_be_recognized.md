---
title: "help getting ext3 drive to be recognized"
date: 2009-05-17
forum: Apple Hardware Users
---

### Post by linuxted on 2009-05-17
I have a linux drive formatted as ext3

How do I get a Mac to recognize it?

If I need to rewrite the data in a different format please give me some pointers (ie. what type and which package would make it easy).


Thanks, 
linuxted

---

### Post by cyberdork33 on 2009-05-18
Try this, though it doesn't work well for most.
[http://sourceforge.net/projects/ext2fsx/](http://sourceforge.net/projects/ext2fsx/)

otherwise just look at another filesystem. 

FAT32 is most compatible, but there is a 4GB filesize limit.

NTFS also can work with all systems, as can unjournaled HFS+

---

