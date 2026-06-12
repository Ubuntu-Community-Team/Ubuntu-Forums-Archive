---
title: "Can't write to newly formated USB drive"
date: 2007-06-10
forum: Absolute Beginner Talk
---

### Post by bruce50 on 2007-06-10
I just formatted an external usb drive using Gparted.  I used ext3 filesystem.  This is a drive that will not be permanently connected to the system but only connected when I want to backup large files (VirtualBox hard drive images to be exact).  I can't copy anything to the drive using the GUI.  I can't even create a folder.  How can I change permissions, ownership or whatever on this disk so I can use it with the GUI every time I plug it in?

here is the fdisk -l listing:

Disk /dev/sdb: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        4864    39070048+  83  Linux

There is no entry for this disk in /etc/fstab

Thanks

---

### Post by taurus on 2007-06-10
What is the mount point for /dev/sdb1?  You need to change the ownership of that mount point from root to your username so you can write to it.  _Assuming_ you mount it to /media/sdb1 and your login name is **bruce**, open a terminal and do

```
sudo chown -R **bruce**:**bruce** /media/sdb1
ls -la /media
```

---

### Post by bruce50 on 2007-06-10
Thanks Taurus, that partially worked

The mount point was /media/disk

After keying in :
sudo chown -R bruce:bruce /media/disk
ls -la /media

I got this listing for the drive in question:
drw-rw-r--  3 bruce bruce  4096 2007-06-10 10:37 disk

I opened the GUI, accessed the disk and was able to right click and see that the 'Create Folder' option was no longer greyed.  I tried to create a folder and got a 'no permissions' related error.  I then went to the permissions tab of the disk's properties window and changed everything to read/write.  Back to the GUI and I was able to both create a folder and copy a folder from the internal drive to the external.  A ls -la /media command showed this:

drwxrwxrwx  4 bruce bruce  4096 2007-06-10 11:32 disk

I unmounted the disk, unplugged it and plugged it back in.  It remounted and I was still able to write to it.  I'm curious to see what will happen after a full system restart.

Thanks again for the help.

---

