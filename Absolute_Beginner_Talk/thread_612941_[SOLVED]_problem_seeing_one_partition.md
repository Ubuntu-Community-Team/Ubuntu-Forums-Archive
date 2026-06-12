---
title: "[SOLVED] problem seeing one partition"
date: 2007-11-14
forum: Absolute Beginner Talk
---

### Post by jmfa59 on 2007-11-14
I have some files in secound hard disk which has two partitions one of them when opening it ask for a password first time I open it after booting.
the other problem when I open from mycomputer icon I can see the files in it but I go Media>the disk I see nothing as if it is empty
THANKS

---

### Post by taurus on 2007-11-14
What partition are we talking here?  Post the output of this command from a terminal here.

Applications -> Accessories -> Terminal
```
sudo fdisk -l <-- Lower case letter l, not number 1.
```

---

### Post by jmfa59 on 2007-11-14
can you post the exact code if the partition is   sdb1
THANKS

---

### Post by taurus on 2007-11-14
Is it ntfs, vfat, or ext3 filesystem?

---

### Post by jmfa59 on 2007-11-14
it is ntfs

---

### Post by taurus on 2007-11-14
Install ntfs-3g driver first.

```
sudo apt-get update
sudo apt-get install ntfs-3g
```
Then, edit /etc/fstab

```
gksudo gedit /etc/fstab
```
and add this line to the end of it.

```
/dev/sdb1   /media/sdb1   ntfs-3g   defaults,locale=en_US.utf8   0   0
```
Save it.  Then, create the new mount point if it hasn't been already created and mount it.

```
sudo mkdir /media/sdb1
sudo mount -t 
df -h
```

---

### Post by jmfa59 on 2007-11-14
taurus
You are great ,works fine.
THANKS

---

