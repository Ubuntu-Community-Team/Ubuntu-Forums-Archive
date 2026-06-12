---
title: "Moving Files"
date: 2008-04-07
forum: Absolute Beginner Talk
---

### Post by noskillz on 2008-04-07
Is there an easy way to grab windows files off of the partition while dualbooting in Ubuntu?

---

### Post by Pierre Lourens on 2008-04-07
This might help:

[http://www.debianadmin.com/mount-your-widows-partitions-and-make-it-readwritable-in-ubuntu.html](http://www.debianadmin.com/mount-your-widows-partitions-and-make-it-readwritable-in-ubuntu.html)

---

### Post by wormser on 2008-04-07
> **noskillz said:**
> Is there an easy way to grab windows files off of the partition while dualbooting in Ubuntu?

Yes, with NTFS.  Applications> Accessories> Terminal

```
sudo apt-get install ntfs-config
```

Applications> System Tools> NTFS Configuration Tool and check write support.  Now you can browse to the drive and copy files.

---

### Post by Inxsible on 2008-04-07
If you are using Gutsy, ntfs support is built in. you don't need to install ntfs-config manually.

---

### Post by twist2b on 2008-04-07
manuelly you just type:
sudo su (to get admin rights)
mv (type path of the file)ONE SPACE(path were you want it)

if there is a space in any parts of the path just add a _ if a file is my documents change it to my_documents

good luck. you have gusty though?

---

