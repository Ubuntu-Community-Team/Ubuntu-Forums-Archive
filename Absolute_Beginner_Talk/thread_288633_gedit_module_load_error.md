---
title: "gedit module load error"
date: 2006-10-30
forum: Absolute Beginner Talk
---

### Post by hnaamyilkemku on 2006-10-30
when i run gedit, i always get the following error:

(gedit:4970): libgnomevfs-WARNING **: Cannot load module `/usr/lib/gnome-vfs-2.0/modules/libcdda.so' (/usr/lib/gnome-vfs-2.0/modules/libcdda.so: cannot open shared object file: No such file or directory)

how can i fix this?

---

### Post by Perfect Storm on 2006-10-30
```
sudo aptitide install libgnome-vfs-common
```
see if it helps.

Also check in that place if is present libcdda.so

better yet, use **nano** to editing stuff with instead.

---

