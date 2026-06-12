---
title: "Activating .avi, .mpeg codecs"
date: 2008-02-25
forum: Absolute Beginner Talk
---

### Post by G!zZm0 on 2008-02-25
I tried to watch a .avi movie, but I couldnt...Any help???

---

### Post by wormser on 2008-02-25
You need to enable the [Medibuntu]("https://help.ubuntu.com/community/Medibuntu#head-7486ed038a9becc1dff10a24cc07a38a00d70e9f") repository.  Then install the following packages.

```
sudo apt-get install w32codecs libdvdcss2
```

---

