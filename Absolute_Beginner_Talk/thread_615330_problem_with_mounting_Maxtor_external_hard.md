---
title: "problem with mounting Maxtor external hard"
date: 2007-11-17
forum: Absolute Beginner Talk
---

### Post by mech2000 on 2007-11-17
I have an error message like when I plug in my external hard drive
"hal-storage-removable-mount-all-options refused uid 1000"

But I can successfully mount other one (different external hard drive). Can anyone give me some suggestions on this? 

FYI: I have mounted this one when I used Ubuntu. Now I'm using Kubuntu. 

Many Thanks.

---

### Post by taurus on 2007-11-17
What's the output of this command from a terminal?

```
sudo fdisk -l
```

---

### Post by mech2000 on 2007-11-17
This is what I got: 
/dev/sdb1               1       19457   156288321    7  HPFS/NTFS

---

### Post by taurus on 2007-11-17
Try

```
sudo apt-get update
sudo apt-get install ntfs-3g
sudo mkdir /media/sdb1 <-- If you get a message saying that you already have /media/sdb1, then don't worry about it.
sudo mount -t ntfs-3g /dev/sdb1 /media/sdb1
ls -la /media/sdb1
```

---

### Post by mech2000 on 2007-11-17
It works well. Thanks man.

---

