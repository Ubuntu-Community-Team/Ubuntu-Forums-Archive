---
title: "Writing to NTFS?"
date: 2006-06-09
forum: Absolute Beginner Talk
---

### Post by r3st on 2006-06-09
Is there any possible way? If so, how?

---

### Post by Jagot on 2006-06-09
[https://wiki.ubuntu.com/NTFSReadWrite](https://wiki.ubuntu.com/NTFSReadWrite)

---

### Post by u.b.u.n.t.u on 2006-06-09
No, is the short answer. Writing to NTFS is operating system dependent. You can if you are on a network, using an ubuntu box networked to a XP box, telling the XP box to write. That works, but no linux can natively write to NTFS. Even reading can be a pain.

NTFS is not that advanced a file system. It suffers from defragmenting of data which ext3 and reiser do not.

---

### Post by r3st on 2006-06-09
it reads NTFS with no problem
actually there is a small problem
i dont want the NTFS partitions showing up on the desktop for ubuntu
how do i remove them?

---

### Post by someusernoob on 2006-06-09
```

gconf-editor /apps/nautilus/desktop 

```
Uncheck volumes_visible. And its all or nothing as far as I know.

---

### Post by Jagot on 2006-06-09
Or you could unmount the volumes.  If they showed up automatically you may need to edit your fstab so they don't automount.

---

### Post by Greevous on 2006-06-09
My probelm seems to lie with permissions; I can't read my NTFS partition in ubuntu because I don't have the permission. Also, neither windows nor ubuntu are allowing me to format a blank space on my drive as FAT32. Does anyone know why this could be?

---

### Post by CompShrink on 2006-06-09
in a terminal, type:

gksudo gedit /etc/fstab

then find the line which says "ntfs" (without "s) and put a # in front of it. Save that and it won't be readable or show up on your desktop next time.

Or, edit the line so that where it says to mount (default is usually /media/hdXY) is changed to some folder not in /mount. For example, create a folder called "windows" in your home folder. Then edit the line with ntfs to change it from:
/media/WHATEVER to /home/USERNAME/windows . If you do this, don't put the # in front. Then it will be easy to find, but isn't on the desktop.

---

