---
title: "Change disk permission to read &amp; write"
date: 2007-10-10
forum: Absolute Beginner Talk
---

### Post by eekfonky on 2007-10-10
I have just formatted a second HDD to ext3 but cannot access it to read or write as don't have permission. Please help I need the extra space

---

### Post by eph1973 on 2007-10-10
is it mounted?

---

### Post by eekfonky on 2007-10-11
yes under /media/hdb1

---

### Post by eph1973 on 2007-10-11
Please post the results of entering these three separate commands in the terminal:
```
ls /media | grep hdb
``````
cat /etc/fstab
``````
blkid
```

---

### Post by eekfonky on 2007-10-13
got it fixed, thank you

---

