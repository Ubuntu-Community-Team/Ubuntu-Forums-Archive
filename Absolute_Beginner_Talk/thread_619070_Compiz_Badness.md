---
title: "Compiz Badness"
date: 2007-11-21
forum: Absolute Beginner Talk
---

### Post by jordank on 2007-11-21
Screwing around with the comjpiz manager, i somehow removed my entire title bars.  So i can no longer exit out of windows, minimize, or even move or resize my windows. anyone know what i toggled with?

---

### Post by jordanmthomas on 2007-11-21
maybe you turned off the window decorations plugin?

---

### Post by DutyDuty on 2007-11-22
It's a little confusing, bear with me. 
```
emerald --replace
```
close that terminal.
```
compiz --replace &
```
close that.
open a new terminal and close it.

---

### Post by Vadi on 2007-11-22
Hehe, you killed your window decorator.

If you have emerald installed, doing **emerald --replace** will work, otherwise, you can do **gtk-window-decorator --replace**.

---

### Post by Aquilastudio.com on 2007-11-22
People always have this problem:

Emerald --replace

Compiz  --replace 

And you mastered it.:guitar:

---

