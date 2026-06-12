---
title: "[SOLVED] how do i chang from  gutsy to xubuntu"
date: 2007-12-04
forum: Absolute Beginner Talk
---

### Post by mick222 on 2007-12-04
can i upgrade gutsy to xubuntu i want to try the xfce desktop

---

### Post by forestpixie on 2007-12-04
you can add xubuntu to your system - but gutsy is the version of all 3

to add xubuntu

```
sudo aptitude install xubuntu-desktop
```

when you log in go to options in bottom left - change session to xfce I believe, then make choice as to whether it logs you into xubuntu normally or for one session

---

### Post by sethvath on 2007-12-04
In terminal 
sudo aptitude install xfce4

that will install xfce and the rest of the core components. Should you want to remove it later on, sudo aptitude purge xfce

---

### Post by mick222 on 2007-12-04
thx wasn't sure thought it would be more complicated than that .

---

### Post by sethvath on 2007-12-04
Stick to forestpixie's method, its simpler to install the prepackaged xunbuntu-desktop

---

