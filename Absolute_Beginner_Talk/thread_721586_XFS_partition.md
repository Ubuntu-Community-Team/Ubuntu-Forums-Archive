---
title: "XFS partition"
date: 2008-03-11
forum: Absolute Beginner Talk
---

### Post by jan-paul on 2008-03-11
Hey, ive partitioned my secondary HD to XFS using GPArted. I can acces the drive (although its empty) but I cant load files on it. It says that i don't have permission to write to the folder.

How can I fix this? 

thx

---

### Post by jan-paul on 2008-03-11
disk properties/permissions - owner,group, and others are unknown and all read-only

---

### Post by justleen on 2008-03-11
you need to give your user access to the disk (its root's by default)
the easiest, if you have a single user system, is give your user the ownership:
```

$ sudo chown user:user /media/disk

```
this will give "user" group and ownership to the disk.

---

### Post by jan-paul on 2008-03-11
> **justleen said:**
> you need to give your user access to the disk (its root's by default)
the easiest, if you have a single user system, is give your user the ownership:
```

$ sudo chown user:user /media/disk

```
this will give "user" group and ownership to the disk.

it didnt work :(
mounted and unmounted

```
 
jan-paul@jan-paul-desktop:~$ $sudo chown jan-paul:jan-paul /media/disk
chown: cannot access `/media/disk': No such file or directory
jan-paul@jan-paul-desktop:~$ $sudo chown jan-paul:jan-paul /media/disk
chown: changing ownership of `/media/disk': Operation not permitted
jan-paul@jan-paul-desktop:~$ 

```

---

### Post by justleen on 2008-03-11
erm, you will have to change "disk" to what ever is your disk.\

assuming it is mounted in /media somewhere..


post the outpout of
```

sudo fdisk -l

sudo mount -l

```

---

### Post by jan-paul on 2008-03-11
I typed a $ to much it works now :)

thx

---

### Post by justleen on 2008-03-11
Duh, sorry missed that :)

np

---

