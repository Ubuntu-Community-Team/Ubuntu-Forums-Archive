---
title: "How to mount a SFS filesystem hard drive in Ubuntu 6.10"
date: 2007-01-13
forum: Absolute Beginner Talk
---

### Post by dustoashes on 2007-01-13
Hi,

While I managed to mount my NTFS partitions, I cannot get my hard drive with the SFS filesystem to mount.  Here's what I've done so far:

> sudo fdisk -l

>  Naprava Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       24321   195358401   42  SFS

> sudo gedit /etc/fstab

> /dev/sdb1 /media/sdb sfs umask=0222 0 0

> sudo mount -a

> mount: unknown filesystem type 'sfs'

---

### Post by dustoashes on 2007-01-13
Lol, the minute I posted it, I tried mounting as a NTFS and it works like a charm. ](*,)

---

