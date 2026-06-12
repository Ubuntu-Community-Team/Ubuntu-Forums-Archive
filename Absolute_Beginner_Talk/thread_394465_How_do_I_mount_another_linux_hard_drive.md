---
title: "How do I mount another linux hard drive"
date: 2007-03-26
forum: Absolute Beginner Talk
---

### Post by Krystoll Meth on 2007-03-26
I have two drives, one running 6.10, one running the beta of 7.04.  How exactly do I mount the drive running 7.04 in the 6.10?  Just so that I can run some files from it.

---

### Post by Krystoll Meth on 2007-03-26
Bumping

---

### Post by murlosad on 2007-03-26
first do this in a terminal:

> cat /etc/fstab

and see if it lists your new drive there.  If it does you can read it by doing:

> sudo mount /dev/hd*

where * = your new drive, for example /dev/hdb1 or /dev/sdc1

once it mounts the drive you can use nautilus or whatever filemanager you choose and navigate to the mount point (probably /media/hd*).

If your drive is not listed in fstab you can still mount it but you will need somemore info.

maybe post the output of 'cat /etc/fstab' and 'cat /etc/mtab'

---

