---
title: "writing to a windows HDD"
date: 2006-08-11
forum: Absolute Beginner Talk
---

### Post by Hg80 on 2006-08-11
hi all i have one final question before i believe myself to be confident in using Ubuntu.

Im trying to write to my windows HDD (Drive c:) but i cant seem to find away of doing so, its located under Ubuntu as /media/sda1 so i have tried
```
hg@hg80:~$ sudo chmod 777 /media/sda1
Password:
chmod: changing permissions of `/media/sda1': Read-only file system
hg@hg80:~$

```

PS its NTFS too

---

### Post by Arisna on 2006-08-11
The "standard" Linux kernel only has read support for NTFS file systems.  However, a project recently developed fairly good facilities for read-write access.  I believe this is the project's page:

[http://www.linux-ntfs.org/](http://www.linux-ntfs.org/)

---

### Post by Hg80 on 2006-08-11
ah ok then i think i will wait till it comes as standard on Ubuntu

---

### Post by Brunellus on 2006-08-11
enabling write access to ntfs under linux is still NOT RECOMMENDED unless you enjoy filesystem corruption.

The usual solution is to create a fat32 partition as a 'share' area between a windows system and a linux system.

---

### Post by Hg80 on 2006-08-11
but the new linux-NTFS is ment to be rather in good, infact its ment to be very stable

---

### Post by Brunellus on 2006-08-11
> **Hg80 said:**
> but the new linux-NTFS is ment to be rather in good, infact its ment to be very stable
are you willing to replace potentially lost data with a little sticky note that reads "this driver was meant to be rather good?"

If that's not an option, then don't use an experimental driver.

---

### Post by stinerman on 2006-08-11
The "stable" driver with write support (Linux-NTFS) is safe to use for read/write operations.  The driver will refuse to delete or write a new file if it detects a condition that would cause any damage to your NTFS partition.  This is not the driver that comes with the kernel, but a driver based on FUSE.  You'll need to install libntfs8 to use it.

So the functionality isn't there, but it is safe to use.

---

### Post by Anduu on 2006-08-11
I have used this method and the older method using ntfs-fuse....they are both quite stable and safe...

Now I wouldn't go so far as to try to rewrite an entire ntfs drive but for day to day copying of mp3s etc I would not hesitate...

---

### Post by xianlee on 2006-08-11
I think you need to unmount it

---

