---
title: "Searching for file by file size"
date: 2007-01-24
forum: Absolute Beginner Talk
---

### Post by bruceathome on 2007-01-24
Hi all.  Is there any way to search for files over a particular size (e.g. list all files over 100MB?).

I have beagle installed, and can't seem to find any way to search by file size.

Thanks,

Bruce

---

### Post by yabbadabbadont on 2007-01-24
```
/home/bubba $ find . -size +100M -print
./temp/wallpaper-sample.tar.bz2
/home/bubba $ ls -lh temp/
total 137M
-rw-r--r-- 1 bubba bubba 137M 2007-01-23 22:22 wallpaper-sample.tar.bz2

```

---

### Post by bruceathome on 2007-01-24
Thanks yabbadabbadont.  Worked a treat.

---

