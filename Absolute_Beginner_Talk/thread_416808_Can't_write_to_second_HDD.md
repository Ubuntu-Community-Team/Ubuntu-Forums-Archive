---
title: "Can't write to second HDD"
date: 2007-04-21
forum: Absolute Beginner Talk
---

### Post by arya6000 on 2007-04-21
Hello

I just formated a new HDD to ext3 and I'm using it as my second HDD for Ubuntu 7.04, but I don't have permission to write to the drive. How can I enable the permission so I can write to the HDD?

Thanks

---

### Post by taurus on 2007-04-21
You can change the ownership of it from root to your username so you can write to it.  _Assuming_ your login name is **arya** and you mount the second drive to **/media/sdb1**, open a terminal and do

```
sudo chown -R **arya**:**arya** **/media/sdb1**
ls -la /media
```

---

