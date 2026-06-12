---
title: "Cant write to shared drive.."
date: 2006-02-28
forum: Absolute Beginner Talk
---

### Post by systemintheglitch on 2006-02-28
I made a shared fat32 drive between windows and ubuntu and i cant write to it from ubuntu but i can from windows..

---

### Post by ubuntuuser on 2006-03-01
Change the corresponding line in /etc/fstab and add umask=000. It should look like this:```
/dev/hda2       /media/transfer  vfat    umask=000        0       0
```

---

### Post by Sutekh on 2006-03-01
You should follow this guide

[http://www.psychocats.net/linux/mountwindows.php]("http://www.psychocats.net/linux/mountwindows.php")

---

