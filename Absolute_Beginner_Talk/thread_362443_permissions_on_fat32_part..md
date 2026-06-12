---
title: "permissions on fat32 part."
date: 2007-02-15
forum: Absolute Beginner Talk
---

### Post by antgul3382 on 2007-02-15
i have a fat32 partition mounted and all and i cant change the permissions so i can write in the folders, it like the whole partition is read only. what do i do?

---

### Post by lamalex on 2007-02-15
```
cat /etc/passwd |grep (your username)
sudo gedit /etc/fdisk
```
change your partition permissions to the uid and gid in /etc/passwd. save and umount [parition] then mount partition.

---

