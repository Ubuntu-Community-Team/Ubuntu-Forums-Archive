---
title: "FAT32 mount point?"
date: 2007-05-11
forum: Absolute Beginner Talk
---

### Post by Karri on 2007-05-11
I'd like to have a fat32 partition on my hard drive to be able to share files between Windows and Ubuntu, since both OS' support read/write on fat32.

So I want both Windows and Ubuntu to recognize the fat32 partition.

What do I set to be the mount point for fat32?
Options:
/
/dos
/windows

?

---

### Post by wormser on 2007-05-11
Are you just starting an install?

---

### Post by Karri on 2007-05-11
Yes, of Ubuntu. Windows XP is already installed.

---

### Post by wormser on 2007-05-11
I believe you do not give it a mount point.  Are you able to do this.  When you log in then you can mount the drive.

---

### Post by Martin on 2007-05-11
you generally put mount poins in /mnt so /mnt/windows or something. Ubuntu seems to also put them mountpoints in /media so it would be /media/windows. I guess either is OK. Could you ut them somewhere else - of course- but I'd stick to convention and put them in /media/

---

### Post by anaconda on 2007-05-11
you can mount it anywhere you want..

but there is another choice. There is a program, that allows windows read/write to your ubuntu (ext3) partition, so separate partition isn't really needed..

---

### Post by Martin on 2007-05-11
I didn't realise you were just starting an install. If you've already got a fat32 partition the install process will rcognise it. It will also recognize your ntfs partitions if you have them and give them read access. Once everything is installed you can then install ntfs-3g have write access to them as well

---

### Post by tact on 2007-05-11
Yep if you are just installing and hve the fat32 partition in place, ubuntu will recognise it and there will be mounts created automatically for it (and any other partitions).   They will be in your desktop waiting for you once install is done.  :)

---

