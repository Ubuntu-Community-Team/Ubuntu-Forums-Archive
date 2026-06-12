---
title: "Help with NTFS-3G"
date: 2007-07-05
forum: Absolute Beginner Talk
---

### Post by creamcheeze77 on 2007-07-05
So i installed NTFS-3G via synaptic, and the drives mounted successfully the first time.  However, attempting to mount them now, either via ntfs-config or by clicking them in file browser, results in the following error:
```
mount_point cannot contain the following characters:newline, G_DIR_SEPARATOR (usually /)
```
this makes no sense, as the mount point (/media/storage) shouldn't have changed.  anyone have any insight here?

---

### Post by creamcheeze77 on 2007-07-05
UPDATE: this problem is sporadic: if i restart, often the drives mount just fine.

---

### Post by zero244 on 2007-07-05
I installed NTFS support via Automatix2 and it has worked flawlessly. Its a two click install.
I have noticed if you have certain errors on the ntfs partition Ubuntu may not mount it.
If your dual booting with Windows do a chkdsk on it and remove any errors. Then see if it mounts in Linux.
Check out the Automatix2 install. The first time I installed ntfs support manually I had to play around with the Fstab file to get Ubuntu to read and write the partition.
With Automatix it configures everything and mounts all partitions automatically.

---

### Post by cwmoser on 2007-07-05
I found that ntfs-3g was kinda quirky ... and it suddenly cleared up when I copied my Ubuntu installation to another partition.  My new partition is on another hard drive and is larger.  Don't have proof this was the reason but now ntfs-3g works flawlessly.  Go figure.

Carl

---

### Post by creamcheeze77 on 2007-07-15
so it's been working perfectly for a week or so, now all of a sudden i can't mount the drive again and sometimes it won't even see it. anyone have any thoughts?
EDIT: it's only the one hard drive (the one i'm trying to use), the error i get is "Mount_point cannot contain the following characters: newline, G_DIR_SEPARATOR (usually /)"

---

### Post by TheExplorer on 2007-07-15
To be able to automatically mount your ntfs partitions with read/write support you should:

Install the following packages with Synaptic:

libfuse2
fuse-utils
libntfs-3g
ntfs-3g
ntfs-config

Then go to Applications -> System Tools -> NTFS Configuration and mount'em all. If you can't in any case mount your windows partition there is a little trick - put a tick in the checkbox, input Windows and then click anywhere inside the list of available partitions and it will be added. Then put the ticks on the next dialog message.

P.S. Ubuntu can't automount ntfs partitions if they had problems starting in windows (or when shut down inappropriately) - chkdsk them and restart. That should solve the problem.

---

### Post by creamcheeze77 on 2007-07-27
chdsk fixed the problem, apparently it was partitioned badly

---

