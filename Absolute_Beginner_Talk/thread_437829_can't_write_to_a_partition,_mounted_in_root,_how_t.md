---
title: "can't write to a partition, mounted in root, how to change?"
date: 2007-05-09
forum: Absolute Beginner Talk
---

### Post by bagbiter on 2007-05-09
How do I change the owner of a partition, so that I can USE it?? 
The partition is mounted in /stuff

and how do I delete folders?

---

### Post by AAM on 2007-05-09
open a terminal and type > sudo nautilus Put in your password and then browse to the partition, right click and change the permissions.

There are command line entries also which you can find with a search of UbunutForums.

---

### Post by Wim Sturkenboom on 2007-05-09
Have a look at the file */etc/fstab*. As an example
```
/dev/cdrom       /mnt/cdrom       iso9660     noauto,owner,ro  0   0
```
Change *owne*r to *user* and the user should be able mount as well.

Ypu do not really specify what kind of partition it is (windows partition?)

PS This comes from a non-Ubuntu box.

---

### Post by bagbiter on 2007-05-09
i fixed it, thanks  alot. it is an ext3 partition

---

