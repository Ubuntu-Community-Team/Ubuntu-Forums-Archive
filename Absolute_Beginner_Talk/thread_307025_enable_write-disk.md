---
title: "enable write-disk"
date: 2006-11-25
forum: Absolute Beginner Talk
---

### Post by oliviacond on 2006-11-25
How to enable write-disk? I got a error message whenever I want to enable it.
> Permission could not be changed
Sorry, couldn't change the permission of "'drive'"


---

### Post by taurus on 2006-11-25
What disk you want to write to and what is the filesystem of it:  ntfs, fat32, ext2, ext3, etc.?

---

### Post by oliviacond on 2006-11-26
the disk is Filesystem and it is ext3

---

### Post by taurus on 2006-11-26
Where is it, i.e. mount point, directory name, etc.?

---

### Post by oliviacond on 2006-11-26
how to check where it is?

---

### Post by taurus on 2006-11-26
Do you mean your extra harddrive/partition?

Applications -> Accessories -> Terminal
```
df -h
```

---

### Post by oliviacond on 2006-11-26
no. it's not extra hdd
The filesystem is /dev/sda1
It is mounted on /

---

### Post by taurus on 2006-11-26
> **oliviacond said:**
> no. it's not extra hdd
The filesystem is /dev/sda1
It is mounted on /
If it is /, then please leave the permissions where they are because changing permissions on / can cause system to crash...  If you need to edit something under /, use the sudo command!!!

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by oliviacond on 2006-11-26
nevermine. But thanks! :)

---

