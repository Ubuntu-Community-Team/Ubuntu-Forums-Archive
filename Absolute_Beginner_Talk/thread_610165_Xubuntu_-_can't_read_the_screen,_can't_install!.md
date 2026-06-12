---
title: "Xubuntu - can't read the screen, can't install!"
date: 2007-11-11
forum: Absolute Beginner Talk
---

### Post by getmeoutofhere on 2007-11-11
I absolutely don't understand why my old laptop doesn't work with Xubuntu (either 7.04 or 7.10).  The screen is a haze of turquoise, which is barely readable.  I've tried to change the resolution - on 7.10 I can find where to do it, I think, but haven't a clue on 7.04, because the 7.04 screen is so bad.  Yet I've tried other operating systems, and they seem to be able to change the resolution to a level that makes the screen quality acceptable.  Any ideas?  My laptop is 2001 vintage, originally packaged with XP, with 250K RAM.  So there really shouldn't be a problem.

---

### Post by taurus on 2007-11-11
At the GUI login screen, press <Ctrl><Alt>F2 to get to another console.  Login and at the prompt, run

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

---

