---
title: "I can't mount my external HDD"
date: 2007-05-27
forum: Absolute Beginner Talk
---

### Post by mrKaqz on 2007-05-27
I can't not mount my External Hard Drive (NTFS)

---

### Post by taurus on 2007-05-27
Try something like

Applications -> Accessories -> Terminal
```
sudo mkdir /media/extra
sudo mount -t ntfs /dev/sda1 /media/extra -o nls=utf8,umask=0222
df -h
```
_Assuming_ /dev/sda1 is your external harddrive.

---

### Post by mrKaqz on 2007-05-27
I can't not mount my External Hard Drive (NTFS)


I already install ntfs-3g and enable read write support for external device

Help me please.

---

