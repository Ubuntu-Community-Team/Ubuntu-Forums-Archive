---
title: "Mounting a Windows Partition"
date: 2007-02-21
forum: Absolute Beginner Talk
---

### Post by kilroy423 on 2007-02-21
After mounting my windows partition by running

```
sudo fdisk -l
```
```
sudo mount /dev/sda1 /home/dan/Desktop/Windows
```

I still cant seem to gain access to that folder....even after running a chmod and chown i cant seem to get permissions to open the contents.

thx,
dan

---

### Post by taurus on 2007-02-21
Is /dev/sda1 ntfs or vfat?

---

### Post by kilroy423 on 2007-02-21
ntfs

---

### Post by mahy on 2007-02-21
This is what works for me (an /etc/fstab entry):

/dev/sda1       /mnt/win        ntfs    umask=0222,nls=utf8,auto,ro     0       0

That's a SATA disk, of course. Good luck!

---

### Post by kilroy423 on 2007-02-21
now what is the command to execute fstab?

---

### Post by taurus on 2007-02-21
```
sudo mount -a
```

---

### Post by kilroy423 on 2007-02-21
```
 cd: /mnt/win: Permission denied
```

still having permission problems

---

### Post by taurus on 2007-02-21
Personally, I would do something like this in /etc/fstab

```
/dev/sda1   /mnt/win   ntfs   nls=utf8,umask=0222   0   0
```

---

### Post by kilroy423 on 2007-02-21
same....cant access because of permissions

---

### Post by taurus on 2007-02-21
Reboot.

---

### Post by punx45 on 2007-02-21
the fstab for my NTFS drive is thus:
```
/dev/hdb1       /media/hdb1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1

```

> I still cant seem to gain access to that folder....even after running a chmod and chown i cant seem to get permissions to open the contents.

did you chmod/chown recursively?
man chmod or chown and scroll to '-R'  for details.

---

### Post by kilroy423 on 2007-02-21
lol...thx...why didnt it work by simply running the mount command?

---

