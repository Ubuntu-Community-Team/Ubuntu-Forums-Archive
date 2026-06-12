---
title: "Xubuntu hangs on startup"
date: 2008-02-20
forum: Absolute Beginner Talk
---

### Post by doctorbighands on 2008-02-20
I have xubuntu installed over the top of Ubuntu Server 7.10 on a legacy machine. Everything seems to have installed properly (finally!), but now it hangs on startup. It gets as far as showing me the wallpaper and an "X" shaped cursor in the middle of the screen, but the GUI won't load any further than that.

Ideas?

---

### Post by doorknob60 on 2008-02-20
How much RAM do you have?

---

### Post by doctorbighands on 2008-02-20
The machine has 426MB RAM. I don't see that that should be the issue...right?

---

### Post by Presto123 on 2008-02-20
Maybe try to reset it to defaults:

```

sudo dpkg-reconfigure -phigh xserver-xorg
```

---

### Post by doctorbighands on 2008-02-20
I restored xorg to defaults, hit CTRL-ALT-BACKSPACE to restart X, and it still gets stuck at the same spot.

*sigh*

---

### Post by doctorbighands on 2008-02-20
*bump*

---

### Post by doctorbighands on 2008-02-21
*bump* again...

---

