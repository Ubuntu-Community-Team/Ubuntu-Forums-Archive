---
title: "stopping X server"
date: 2006-11-14
forum: Absolute Beginner Talk
---

### Post by mongooseman1128 on 2006-11-14
What's the command to stop X server? I tried init 3 but that definitely wasn't it.

---

### Post by jordanmthomas on 2006-11-14
init 3 should stop X, but here's what I usually do when using Ubuntu
```
sudo /etc/init.d/gdm stop
```
...assuming you are in fact using gdm


...oh, and 
```
sudo gdm
```
will bring it back when you are ready.

---

### Post by mongooseman1128 on 2006-11-14
awesome, thanks

---

### Post by Dual Cortex on 2006-11-14
CTRL+ALT+F1 then _if you use gdm_
```
sudo /etc/init.d/gdm stop
```
or if you use kdm:
```
sudo /etc/init.d/kdm stop
```

---

