---
title: "Partition keeps coming up r/o"
date: 2007-05-14
forum: Absolute Beginner Talk
---

### Post by dbvanhorn on 2007-05-14
I rebuilt my 500g drive this weekend, from NTFS to reiserfs.

Everything seemed ok, up to the point where I have it mounted and I start trying to move files back to it.
After boot, the partition is there, under /media/sdd1 and is r/w
If I start moving files to it, that will proceed for a while, then give me I/O errors, and when I check, the partition is then read only.

What's going on?   Testdisk says its ok, but I keep hitting this wall.

---

### Post by taurus on 2007-05-14
How do you mount /dev/sdd1?  If you mount it from /etc/fstab, can you post it here?

```
cat /etc/fstab
ls -la /media
```

---

### Post by dbvanhorn on 2007-05-14
This is from AFTER it's flipped to ro again.
If I chmod it back to r/w, it will seem to be ok again, for a while, then back to read only.


/dev/sdb1                                  /media/sdb1     reiserfs     defaults                     0  0  
/dev/sdc1                                  /media/sdc1     reiserfs     defaults                     0  0  
/dev/sdd1                                  /media/sdd1     reiserfs     defaults                     0  0  
/dev/sda1                                  /media/sda1     ext3         defaults                     0  0  
/dev/sda5                                  /media/sda5     swap         defaults                     0  0  


total 115
drwxr-xr-x 12 root root  4096 2007-05-14 09:11 .
drwxr-xr-x 22 root root  4096 2007-05-06 12:21 ..
lrwxrwxrwx  1 root root     6 2007-05-05 08:58 cdrom -> cdrom0
drwxr-xr-x  2 root root  4096 2007-05-05 08:58 cdrom0
drwxr-xr-x  2 root root  4096 2007-05-05 08:58 cdrom1
lrwxrwxrwx  1 root root     7 2007-05-05 08:58 floppy -> floppy0
drwxr-xr-x  2 root root  4096 2007-05-05 08:58 floppy0
-rw-r--r--  1 root root     0 2007-05-14 09:11 .hal-mtab
-r-Sr-----  1 root root     0 2007-04-15 08:03 .hal-mtab-lock
drwxrwxrwx  1 root root 81920 2007-05-13 22:42 hdc1
drwxr-xr-x 22 root root  4096 2007-05-06 12:21 sda1
drwxr-xr-x  2 root root  4096 2007-05-13 21:57 sda5
drwxr-xrwx  8 root root   184 2007-05-14 08:39 sdb1
drwxr-xrwx 33 root root  1712 2007-05-13 23:18 sdc1
drwxr-xrwx  7 root root  1472 2007-05-13 19:44 sdd1
drwxr-xr-x  2 root root  4096 2007-05-05 18:51 sdg1

---

