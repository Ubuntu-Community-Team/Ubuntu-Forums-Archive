---
title: "is there a way for me to convert ext3 to ext4 without loosing any files"
date: 2007-08-26
forum: Absolute Beginner Talk
---

### Post by cosmoshell on 2007-08-26
is there a way for me to convert ext3 to ext4 without loosing any of my files. if not how can i create a ext4 partition in gusty

---

### Post by AlexenderReez on 2007-08-26
as far as i know..gparted only provided way to convert ext2 and ext3...just wait then....but obviously if you want to change kind ofpartition..you need to format it...

---

### Post by Steveway on 2007-08-26
You should alway first do research before you post a question.
Wikipedia:
> Backward compatibility

The ext4 filesystem is backward compatible with ext3, making it possible to mount an ext3 filesystem as ext4 (using the &#8220;ext4dev&#8221; filesystem type).

[edit] Forward compatibility

The ext4 filesystem is forward compatible with ext3, that is, it can be mounted as an ext3 partition (using &#8220;ext3&#8221; as the filesystem type when mounting). However, if the ext4 partition uses extents (one of the major new features of ext4), forward compatibility and therefore the ability to mount the filesystem as ext3 is lost. Extents are not used by default; the &#8220;extents&#8221; option is explicitly required (e.g. mount /dev/sda1 /mnt/point -t ext4dev -o extents

---

### Post by schorsch on 2007-08-26
> **cosmoshell said:**
> is there a way for me to convert ext3 to ext4 without loosing any of my files. if not how can i create a ext4 partition in gusty
I just found this:
```
Backward compatibility

The ext4 filesystem is backward compatible with ext3, making it possible to mount an ext3 filesystem as ext4 (using the &#8220;ext4dev&#8221; filesystem type).
```
[here]("http://en.wikipedia.org/wiki/Ext4")....

EDIT: well, beaten again....

---

### Post by cosmoshell on 2007-08-26
how can i make an ext4 partition

---

### Post by Steveway on 2007-08-26
Dude are you listening?
We told you everything.
Just make your ext3 Partition and mount it using ext4dev instead of ext3.
You need ofcourse ext4-support in your kernel.

---

### Post by cosmoshell on 2007-08-26
how can i get ext4-support for my kernel

---

### Post by schorsch on 2007-08-26
Have you ever read the links we gave you?
It is not available in the precompiled kernel but it is the kernel sources under "
/usr/src/linux-source-2.6.20/fs/ext4".
So you have to compile your own kernel to get ext4-support.

---

