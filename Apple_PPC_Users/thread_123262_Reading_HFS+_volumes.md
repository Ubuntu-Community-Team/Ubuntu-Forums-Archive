---
title: "Reading HFS+ volumes?"
date: 2006-01-29
forum: Apple PPC Users
---

### Post by llanitedave on 2006-01-29
I've set up a dual boot on my Sept. 2005 iBook with OS X 10.4 and kubuntu 5.10.  I'd like to use kubuntu as my primary system, but there are a fair number of documents on the HFS+ partition that I would like to have access to, and my wife, who uses only the Mac side, would like me to copy some things from the ext2 volume to hers.

Rumor has it that Linux can in principle read HFS+ volumes.  Is there some way to do this with ubuntu?

---

### Post by sonofcolin on 2006-01-29
This maybe a good starting point:
[http://www.ardistech.com/hfsplus/]("http://www.ardistech.com/hfsplus/")

---

### Post by linear on 2006-01-29
Easier yet. This thread will tell you how:

[http://ubuntuforums.org/showthread.php?t=88590](http://ubuntuforums.org/showthread.php?t=88590)

---

### Post by spaceballl on 2006-01-30
I just do this

sudo mount -t hfsplus /dev/hda3 /mnt/osx

that command puts my mac drive in the folder /mnt/osx

so yah. That's only for reading. Still doing more research on how to set up the whole read/write thing :)

-Kevin

---

### Post by llanitedave on 2006-01-30
Thanks guys -- that's exactly what I need.

---

