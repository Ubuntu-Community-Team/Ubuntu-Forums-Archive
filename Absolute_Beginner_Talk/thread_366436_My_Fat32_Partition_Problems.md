---
title: "My Fat32 Partition Problems"
date: 2007-02-20
forum: Absolute Beginner Talk
---

### Post by surautomatism on 2007-02-20
This is probably a rather obvious answer and I'll feel stupid later for asking, but I'm sure you guys can help me. I have the following set up on my computer

sda1 (ntsf, windows xp pro) ~50 gig
sda2 (fat32, shared) ~100 gig
sda3 (ext3, ubuntu 6.10) ~98 gig
sda4 (swap) ~2gig

I set this all up with gparted on the Ubuntu installer (except I had already made a windows partition on that installer, which probably makes no difference) and it did not mount my shared partition. Everything else is fine. I tried to mount it in fstab. Here's that file now:

# /etc/fstab: static file system information.
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc defaults 0 0
# /dev/sda3
UUID=6effc5de-3266-4a87-a7d5-9fe8743b7294 / ext3 defaults,erro$
# /dev/sda1
UUID=64F46444F4641A96 /media/sda1 ntfs defaults,nls=utf8,umask=007,gid=4$
# /dev/sda4
UUID=c80b11ae-2aeb-4854-8524-ba4e866e40cc none swap sw $
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto 0 0
/dev/ /media/floppy0 auto rw,user,noauto 0 0
*/dev/sda2 /media/sda2 vfat iocharset=utf8,rw,users,gid=users,umask=000, 0 0*

I went in to check it (as per this tutorial [http://ubuntuforums.org/showthread.php?t=363565](http://ubuntuforums.org/showthread.php?t=363565)) and I got the message that media/sda2 does not exist. That was in the terminal. I went in to gparted to check and I got a similar message. Do I need to create this folder, and how do I do that?

---

### Post by logos34 on 2007-02-20
> Do I need to create this folder, and how do I do that?

[B]sudo mkdir /media/sda2
sudo mount -a[/B]

---

### Post by dcstar on 2007-02-20
> **surautomatism said:**
> This is probably a rather obvious answer and I'll feel stupid later for asking, but I'm sure you guys can help me. I have the following set up on my computer
.....
I went in to check it (as per this tutorial [http://ubuntuforums.org/showthread.php?t=363565](http://ubuntuforums.org/showthread.php?t=363565)) and I got the message that media/sda2 does not exist. That was in the terminal. I went in to gparted to check and I got a similar message. **Do I need to create this folder**, and how do I do that?

Yes
```
**sudo mkdir /media/sda2**
```

A mount point can be anywhere, you (if you like) could do this:
```
**sudo mkdir /Dos**
``` and change the fstab file to suit, then your Dos disk will be mounted as /Dos on your filesystem.

---

