---
title: "installing files"
date: 2007-05-14
forum: Absolute Beginner Talk
---

### Post by Jorge32 on 2007-05-14
can anybody please explain me how to install files with this extentions?


.tar.bz2

.tar.gz

thanks

---

### Post by taurus on 2007-05-14
```
tar xvjf filename.tar.bz2
tar xvzf filename.tar.gz
```

[http://monkeyblog.org/ubuntu/installing/#source](http://monkeyblog.org/ubuntu/installing/#source)

---

### Post by earobinson on 2007-05-14
your best to try and find a deb package if you can.

---

### Post by Jorge32 on 2007-05-14
and what if for example the file is in a folder in a hardisk different from where home folder is ?

for example in the folder "programas linux" in the sda3 hd?

---

### Post by taurus on 2007-05-14
```
cd the_mount_point_for_/dev/sda3
sudo tar xvjf filename.tar.bz2
-or-
sudo tar xvzf filename.tar.gz
```

---

