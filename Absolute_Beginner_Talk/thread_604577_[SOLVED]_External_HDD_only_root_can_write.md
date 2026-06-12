---
title: "[SOLVED] External HDD only root can write"
date: 2007-11-06
forum: Absolute Beginner Talk
---

### Post by mouko on 2007-11-06
I'm having a problem with my external HDD where it says that only root can write to it.  I did "sudo chmod 777 disk" where disk is the name of the drive, but it still does not let me write to it, giving me a "Permission Denied" error.  Anyone know how I can fix this?  Heck, I could just format the thing, but haven't ever done that from a linux command line.

---

### Post by Dr Small on 2007-11-06
I am sorry. You left no message or explanation of your problem.
I can not assist you.

Dr Small

---

### Post by taurus on 2007-11-06
What filesystem is that external harddrive:  vfat/fat32, ntfs, ext3, etc.?

---

### Post by mouko on 2007-11-06
ext3.  The problem is fixed.  I unmounted, rebooted, and then mounted it, and now it seems to be happy.  Not sure why it didn't work in the first place, but whatever.  Now I've just got to figure out how to mount and unmount it from bash... (Well, I don't *have* to, but it'd probably be a good thing to know.)

---

### Post by Dr Small on 2007-11-06
Good job. ;)
Please mark this thread as solved from Thread tools!

Dr Small

---

