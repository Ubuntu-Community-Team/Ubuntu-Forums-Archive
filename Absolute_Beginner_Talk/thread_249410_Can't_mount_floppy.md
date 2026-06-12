---
title: "Can't mount floppy"
date: 2006-09-02
forum: Absolute Beginner Talk
---

### Post by fzf3 on 2006-09-02
tm@tm-ubuntu:~$ sudo mkfs /dev/fd0
Password:
mke2fs 1.38 (30-Jun-2005)
Filesystem label=
OS type: Linux
Block size=1024 (log=0)
Fragment size=1024 (log=0)
184 inodes, 1440 blocks
72 blocks (5.00%) reserved for the super user
First data block=1
1 block group
8192 blocks per group, 8192 fragments per group
184 inodes per group

Writing inode tables: done
Writing superblocks and filesystem accounting information: done

This filesystem will be automatically checked every 20 mounts or
180 days, whichever comes first.  Use tune2fs -c or -i to override.
tm@tm-ubuntu:~$ sudo mount /media/floppy0
mount: can't find /media/floppy0 in /etc/fstab or /etc/mtab

---

### Post by HAARP on 2006-09-02
Try ```
sudo mount /dev/fd0 /media/floppy0
```

---

### Post by fzf3 on 2006-09-02
Thanks, but it didn't work either:


tm@tm-ubuntu:~$ sudo mount /dev/fd0/media/floppy0
mount: can't find /dev/fd0/media/floppy0 in /etc/fstab or /etc/mtab

---

### Post by HAARP on 2006-09-02
You forgot the space between **fd0** and **/media**

---

### Post by fzf3 on 2006-09-02
tm@tm-ubuntu:~$ sudo mount /dev/fd0 /media/floppy0
mount: mount point /media/floppy0 does not exist

---

### Post by HAARP on 2006-09-02
Create the directory to mount into first with
```
sudo mkdir /media/floppy0
```

---

### Post by fzf3 on 2006-09-02
Thanks!  That worked.

---

