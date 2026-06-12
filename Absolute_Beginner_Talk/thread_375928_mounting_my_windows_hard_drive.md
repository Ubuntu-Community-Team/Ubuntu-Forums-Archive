---
title: "mounting my windows hard drive"
date: 2007-03-04
forum: Absolute Beginner Talk
---

### Post by Milner_07 on 2007-03-04
I would like to mount my windows SATA Hard Drive in Ubuntu. 

Ive done an fdisk and its called Sda1. but i need to put that in my fstab. so how can i do that?

TM
P.s its nfts format (or something like that)

---

### Post by taurus on 2007-03-04
Edit /etc/fstab

Applications -> Accessories -> Terminal
```
sudo cp /etc/fstab /etc/fstab.bak
gksudo gedit /etc/fstab
```
and add this line to the end of it.

```
/dev/sda1   /media/sda1   ntfs   nls=utf8,umask=0222   0   0
```
Save it.  Now, create a new mount point and mount it.

```
sudo mkdir /media/sda1
sudo mount -a
df -h
```

---

### Post by Milner_07 on 2007-03-04
thanks you!!!

That worked like a charm!

TM

---

