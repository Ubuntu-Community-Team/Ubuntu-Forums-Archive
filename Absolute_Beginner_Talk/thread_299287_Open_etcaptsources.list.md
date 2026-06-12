---
title: "Open /etc/apt/sources.list"
date: 2006-11-13
forum: Absolute Beginner Talk
---

### Post by OptimusPrime on 2006-11-13
Just a quick question, what is the code to open /etc/apt/sources.list
and modify it?  I can never remember.

---

### Post by podunk on 2006-11-13
For Ubuntu
gksu gedit /etc/apt/sources.list

Kubuntu:

kdesu kate /etc/apt/sources.list

---

### Post by user1397 on 2006-11-13
> **OptimusPrime said:**
> Just a quick question, what is the code to open /etc/apt/sources.list
and modify it?  I can never remember.on ubuntu: ```
gksudo gedit /etc/apt/sources.list
```on kubuntu: ```
kdesu kate /etc/apt/sources.list
```

damn, beat me to it! :)

---

### Post by grim918 on 2006-11-14
if your working in terminal mode then use```
sudo vim /etc/apt/sources.list
```

or you can use```
sudo nano /etc/apt/sources.list
```

---

