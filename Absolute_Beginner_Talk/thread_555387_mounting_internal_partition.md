---
title: "mounting internal partition"
date: 2007-09-20
forum: Absolute Beginner Talk
---

### Post by muuwt1 on 2007-09-20
i looked around on other threads to figure out how to do this. most of the suggestions have the command
```

fdisk -l 

```
in it somewhere. when i type fdisk -l into my terminal nothing happens. so naturally im stuck  as to where i go from there. i recently changed from XP where i used the internal partition just as a storage for all my internet junk. i need my internet junk back and its not registering for me on Ubuntu.

please advice
most terminal code is over my head so please be specific.
thaaaaaanks
muuwt

---

### Post by yabbadabbadont on 2007-09-20
```
sudo fdisk -l
```
A normal user can't run it, so you have to use sudo to get any output.

---

