---
title: "Mounting a drive"
date: 2007-03-31
forum: Absolute Beginner Talk
---

### Post by danbrownlow on 2007-03-31
Hey, I'm booting up Unbuntu from the Live CD and i'm trying to mount my hard-drive, but I don't know how to do it :( Could anyone tell me how to do it please?
Thanks in advance, Dan

---

### Post by taurus on 2007-03-31
Assuming it's /dev/hda1 with ntfs filesystem, open a terminal and run

Applications -> Accessories -> Terminal
```
sudo mkdir /media/windows
sudo mount -t ntfs /dev/hda1 /media/windows -o nls=utf8,umask=0222
ls -la /media/windows
```

---

### Post by ianb72 on 2007-04-20
How do I mount a Linux partition on the Live CD??

---

### Post by taurus on 2007-04-20
Applications -> Accessories -> Terminal
```
sudo mkdir /media/linux
sudo mount -t ext3 /dev/hda1 /media/linux
df -h
```
Assuming /dev/hda1 with ext3 filesystem is what you want to mount.

---

