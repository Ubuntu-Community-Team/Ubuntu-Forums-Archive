---
title: "mounting with fstab"
date: 2007-01-16
forum: Absolute Beginner Talk
---

### Post by carverj on 2007-01-16
Just wondering why I cannot use the same line I used in Breezy to mount my slave partitions
eg, /dev/hdb1 /media/hdb1 ntfs defaults  0 2
Is it something to do with UUID labels??
Thanks

---

### Post by kidders on 2007-01-16
Hi there,

Why can't you use that line? (What error do you get?)

---

### Post by pay on 2007-01-16
That line should work but make sure that you have the folder created```
sudo mkdir /media/hdb1
```and then remount```
sudo mount -a
```

---

### Post by taurus on 2007-01-16
```
/dev/hdb1   /media/hdb1   ntfs   nls=utf8,umask=0222   0  0
```

---

