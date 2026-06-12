---
title: "Mount Disk on Desktop"
date: 2008-03-26
forum: Absolute Beginner Talk
---

### Post by gallam on 2008-03-26
I have a second disk drive installed in my computer.  It is sdb1.

I used the chown command to make sure I have permissions for the disk.

It mounts at media/sdb1.

My question is, how can I change where it mounts?  For instance, my file system displays a disk icon on the desktop.  If I plug in a USB drive, it displays an icon on the desktop of a usb disk.

sdb1, however, does not show any disk icon at all.  I can only get to it/find it using the file browser by going to file system --> media.

Is there a way to make it show up as a disk on the desktop like the other drives do?

Thanks!

---

### Post by glennric on 2008-03-26
Are automounting this drive via fstab?  There does not seem to be an easy way to have a fixed drive show up on the desktop in the same way that a removable drive does.  However, if this really is a fixed drive you could just make a link to the mount point on your desktop.  
To do this type
```
ln -s /media/sdb1 ~/Desktop/sdb1
```

---

### Post by wormser on 2008-03-26
Mount points in /media should show up on the desktop when mounted.  Did you have this problem before using chown?  Can you post the permissions for the mount point and /ect/fstab.

```
ls -la /media/
```

```
less /etc/fstab
```

---

### Post by gallam on 2008-03-27
Guys, thanks for the replies.  I feel a bit silly.  It did show up before chown, but here is the part that makes me feel silly.

After I restarted the machine, it appeared on the desktop like the other drives.

Sorry for the bother but thanks for the help!

Much appreciated!

---

