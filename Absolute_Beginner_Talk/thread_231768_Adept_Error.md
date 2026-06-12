---
title: "Adept Error"
date: 2006-08-07
forum: Absolute Beginner Talk
---

### Post by calvinthomas on 2006-08-07
Ok, now for some reason I have an annoying error, everytime I start update manager or adept it tells me another process is using package database system and tells me to close all other instances of adept etc, however this happens immediately even after a restart and I can't see any other apps open! Is there a way I can see other apps open (Like a processes manager) or something I can do to fix this?

Calv

---

### Post by ThrobbingBrain66 on 2006-08-07
Kmenu>System>KsysGuard

there is a processes tab that you show you what you want.  btw, have you tried

```
sudo dpkg --reconfigure -a
```

---

### Post by calvinthomas on 2006-08-07
I just found that command and that fixed it! Thanks for the info!

Calv

---

