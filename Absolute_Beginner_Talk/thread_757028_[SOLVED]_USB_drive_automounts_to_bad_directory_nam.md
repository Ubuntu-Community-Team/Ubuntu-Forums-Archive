---
title: "[SOLVED] USB drive automounts to bad directory name"
date: 2008-04-16
forum: Absolute Beginner Talk
---

### Post by bhold on 2008-04-16
I have a Maxtor OneTouch4 USB drive, 250GB. First time I plugged it into my Ubuntu 7.10 system I got a popup message (from gnome vol manager??) telling me to issue the following command...

sudo mount -t ntfs-3g /dev/sdb1 /media/OneTouch4 -o force

OK, I did so and everything worked fine. I then wrote some backup scripts referencing the device mount point directory /media/OneTouch4.

However, from then on every time I plug in the device it mounts automatically to /media/OneTouch4_ instead of /media/OneTouch4

Where is the underscore at the end of the directory name coming from? In case it matters, there is a OneTouch4 directory at /media/, I don't recall whether or not I created it with a mkdir

ls -l /media
total 20
lrwxrwxrwx 1 root root    6 2007-08-28 07:32 cdrom -> cdrom0
drwxr-xr-x 2 root root 4096 2007-08-28 07:32 cdrom0
drwxr-xr-x 2 root root 4096 2007-08-28 07:32 DellUtility
drwxr-xr-x 2 root root 4096 2008-04-08 08:06 OneTouch4
drwxr-xr-x 2 root root 4096 2007-08-28 07:32 OS
drwxr-xr-x 2 root root 4096 2007-08-28 07:32 sda6

---

### Post by seepage87 on 2008-04-17
Did your device ever get renamed, e.g. in windows you hit a space while the rename field was active or something?  Something similar happened to me (though it was more intentional).  Maybe connect it to a windows box and see what happens there, see what it's called.

---

### Post by ace007 on 2008-04-17
the issue is because you made a directory with that name. When you plug it in, Ubuntu tries to create a folder to mount it to, but there is already a folder with the name.  so it add the "_". Try deleting the folder.

---

### Post by bhold on 2008-04-18
Removing the /media/OneTouch4 directory worked - solved.

---

