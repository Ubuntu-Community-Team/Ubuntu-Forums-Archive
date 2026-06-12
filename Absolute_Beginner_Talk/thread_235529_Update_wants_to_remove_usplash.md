---
title: "Update wants to remove usplash"
date: 2006-08-13
forum: Absolute Beginner Talk
---

### Post by PingunZ on 2006-08-13
when I do an upgrade I get this
```
The following packages are unused and will be REMOVED:
  usplash

```
I use usplash so ..
How can I let the updates not remove usplash ?

---

### Post by Ziox on 2006-08-13
> **PingunZ said:**
> when I do an upgrade I get this
```
The following packages are unused and will be REMOVED:
  usplash

```
I use usplash so ..
How can I let the updates not remove usplash ?

did you use sudo aptitude dist-upgrade or did you use apt-get?

---

### Post by PingunZ on 2006-08-13
aptitude

---

### Post by PingunZ on 2006-08-13
hehe app it works with apt-get..
How can I fix it with aptitude ?

---

### Post by Ziox on 2006-08-13
> **PingunZ said:**
> hehe app it works with apt-get..
How can I fix it with aptitude ?

There's away to lock the version of usplash or something, read aptitude's manual:

man aptitude

or

info aptitude

---

