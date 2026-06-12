---
title: "hda6 only readable, no write EXT3"
date: 2007-04-20
forum: Absolute Beginner Talk
---

### Post by Dcox on 2007-04-20
Hi,

I installed ubuntu and there was one big partition of 200Gb. Afterwards I have repartitioned it to 15Gb boot and 150Gb data partition. It is mounted under /media/disk, however in read-only.

How to make it writeable ? It's EXT3 by the way.

Thanks!

---

### Post by sad_iq on 2007-04-20
Type **mount** in a terminal and post the output here!!!

---

### Post by taurus on 2007-04-20
You can change the ownership of that mount point from root to what your login name.  Assuming your login name is **dcox**, open a terminal and do

```
sudo chown -R **dcox**:**dcox** /media/disk
ls -la /media
```

---

### Post by Dcox on 2007-04-20
dieter@Ubuntu:~$ sudo chown dieter:dieter /media/disk/
dieter@Ubuntu:~$ ls -la /media/
total 24
drwxr-xr-x  5 root   root   4096 2007-04-20 17:39 .
drwxr-xr-x 21 root   root   4096 2007-04-20 17:32 ..
lrwxrwxrwx  1 root   root      6 2007-04-20 18:23 cdrom -> cdrom0
drwxr-xr-x  2 root   root   4096 2007-04-20 18:23 cdrom0
drwxrwxrwx  3 dieter dieter 4096 2007-04-20 17:35 disk
lrwxrwxrwx  1 root   root      7 2007-04-20 18:23 floppy -> floppy0
drwxr-xr-x  2 root   root   4096 2007-04-20 18:23 floppy0
-rw-r--r--  1 root   root     51 2007-04-20 17:39 .hal-mtab
--wxr-x---  1 root   root      0 2007-04-15 13:56 .hal-mtab-lock
dieter@Ubuntu:~$ 
----

Writable now!!!
Damn you guys are fast or my questions are really noob :)

Thanks a million

---

### Post by Dcox on 2007-04-21
OK, so i managed to get /dev/hda6 mount on /media/disk.
But I want to let it mount on startup ... 

added

/dev/hda6 /media/disk 

to fstab, does not seem to work...

Any help on this ?

Thanks!

---

