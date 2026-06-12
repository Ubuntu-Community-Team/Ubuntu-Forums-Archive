---
title: "How to change the windows manager."
date: 2007-06-16
forum: Absolute Beginner Talk
---

### Post by microsoft92sucks on 2007-06-16
Well I'm trying to get compiz to work. Here's what happens when I try to run it. So please help on fixing this.
```
ubuntu@ubuntupc:~$ compiz
/usr/bin/compiz.real: Screen 0 on display ":0.0" already has a window manager; try using the --replace option to replace the current window manager.
/usr/bin/compiz.real: No manageable screens found on display :0.0
Window manager warning: Screen 0 on display ":0.0" already has a window manager; try using the --replace option to replace the current window manager.

```

---

### Post by pete83 on 2007-06-16
Try telling compiz to replace the current window manager, like so:

```
compiz --replace
```

---

