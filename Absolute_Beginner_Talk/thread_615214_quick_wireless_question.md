---
title: "quick wireless question"
date: 2007-11-16
forum: Absolute Beginner Talk
---

### Post by TadH on 2007-11-16
hey guys, my wireless works fine and all ...when im at home, it auto detects the unsecured singal and im on, no problem. but my question is, when im out and about how do mi view all of the available networks?, am i mising something easy or is there a process? thanks

---

### Post by oilchangeguy on 2007-11-16
> **TadH said:**
> hey guys, my wireless works fine and all ...when im at home, it auto detects the unsecured singal and im on, no problem. but my question is, when im out and about how do mi view all of the available networks?, am i mising something easy or is there a process? thanks

install wi-fi radar. it's in add/remove. or synaptic.

---

### Post by finer recliner on 2007-11-16
```
iwlist eth1 scan
```

---

### Post by oilchangeguy on 2007-11-16
> **finer recliner said:**
> ```
iwlist eth1 scan
```

no, it's, iwlist wlan0 scan
and this does not enable you to connect to what's available. so therefore, it's useless.

---

