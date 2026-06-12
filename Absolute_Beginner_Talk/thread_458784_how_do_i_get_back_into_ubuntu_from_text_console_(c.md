---
title: "how do i get back into ubuntu from text console (ctrl+alt+Fn) (f1,f2...)"
date: 2007-05-30
forum: Absolute Beginner Talk
---

### Post by bishop9226 on 2007-05-30
thx

---

### Post by Tux Aubrey on 2007-05-30
Ctrl-Alt-F7

---

### Post by RomeReactor on 2007-05-30
Hi. Try **CTRL+ALT+F7**.

---

### Post by tgalati4 on 2007-05-30
startx

---

### Post by bishop9226 on 2007-05-30
ctrl alt f7 just gives me a black screen with a moving mouse, then i have to reboot!!

---

### Post by bishop9226 on 2007-05-30
nm it works, thanks!

---

### Post by mkoehler on 2007-05-30
Also, if that ever fails for you, you can do either:

```
/etc/init.d/gdm restart
```

if you're running GDM, or

```
/etc/init.d/kdm restart
```

if you're running KDM

---

### Post by Crafty Kisses on 2007-05-30
> **bishop9226 said:**
> thx

There's a lot of different methods, I believe they're all mentioned in this thread. Ctrl+Alt+F7 works the best for me.

---

