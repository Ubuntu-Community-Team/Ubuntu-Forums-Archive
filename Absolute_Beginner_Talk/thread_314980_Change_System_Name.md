---
title: "Change System Name"
date: 2006-12-08
forum: Absolute Beginner Talk
---

### Post by Captain Kirk76 on 2006-12-08
How do i rename my system? I.E give my system a customized name like "Yoda"

---

### Post by taurus on 2006-12-08
Make the change to **_both_** /etc/hosts & /etc/hostname...

Applications -> Accessories -> Terminal
```
gksudo  gedit  /etc/hostname  /etc/hosts
```

---

### Post by CatKiller on 2006-12-08
Or graphically with System -> Networking -> General -> Hostname

---

