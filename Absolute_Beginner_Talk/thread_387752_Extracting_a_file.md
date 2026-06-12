---
title: "Extracting a file"
date: 2007-03-18
forum: Absolute Beginner Talk
---

### Post by ajeffreys on 2007-03-18
I try to extract a file to /opt, but it says i don't have permission. How to i get around this.

Thanks,
Ajeffreys

---

### Post by bernied on 2007-03-18
Use sudo
```
sudo tar ...
```

---

### Post by PartisanEntity on 2007-03-18
You could extract it as root. Press ALT-F2 and then type gksudo-nautilus then click on 'Run'.

A window will pop up, then you can do the moving and unzipping from this window. If you close this window you will be back to your normal user permissions.

---

### Post by bernied on 2007-03-18
Or, if you're using nautilus, run a session of nautilus as root:
```
gksudo nautilus
```
You can make a menu entry for this, can come in handy.

---

