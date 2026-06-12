---
title: "FSCK issues"
date: 2007-06-07
forum: Absolute Beginner Talk
---

### Post by Yxven on 2007-06-07
When I run fsck -n, when everything is loaded and the harddrive is mounted, it says there are loads of problems on my first harddrive.

When I reboot my computer into safemode, umount that harddrive, it says it's clean (although it says it instantly, it doesn't seem to check anything).

Are there problems on my first harddrive or not?

---

### Post by dmfield on 2007-06-08
Probably yes.. last time i had a Hard disk problem, t[his page was useful]("http://www.linuxjournal.com/article/193").. sorry can't be more help..

---

### Post by daschmidty on 2007-06-08
Also just a heads up....
```
david@DAVID-DESKTOP:~$ sudo fsck -n /dev/md0
Password:
fsck 1.40-WIP (14-Nov-2006)
fsck.jfs version 1.1.11, 05-Jun-2006
processing started: 6/8/2007 17.9.21
Filesystem is currently mounted.
**WARNING: Checking a mounted filesystem does not produce dependable results.**
```

so the problems may be nonexistent

---

### Post by manual_overide on 2007-06-08
Yes, you really should never run fsck on a live filesystem unless it's an emergency.  A safer bet would be to boot from your CD and run fsck on the harddisk from there.

---

