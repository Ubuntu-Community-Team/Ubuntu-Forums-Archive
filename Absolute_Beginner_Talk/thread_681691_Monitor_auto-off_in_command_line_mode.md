---
title: "Monitor auto-off in command line mode"
date: 2008-01-29
forum: Absolute Beginner Talk
---

### Post by tuoepiw on 2008-01-29
Hi,

I recently installed Ubuntu on my Macbook for the purpose of dedicated folding. After some reading i've decided to run Ubuntu in command line mode (CTRL+ALT+F1 @ Login) in hopes of maybe pushing out a few more PPD. However now the monitor no longer turns off after 1 minute like i have it set to in the GUI (screen saver disabled) Is there anyway to get the monitor to turn off after X minutes from the command line mode?

Thanks heaps.

BTW: I tried searching, but didn't get exactly what i wanted, maybe I'm a poor searcher :(

---

### Post by shae on 2008-01-29
```
xset dpms off *time*
```

IIRC

---

### Post by tuoepiw on 2008-01-29
Hrm, thanks for the reply but that gives me...

```
xset: unable to open display ""
```

---

