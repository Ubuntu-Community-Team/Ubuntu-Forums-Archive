---
title: "Ummm Help?"
date: 2007-04-29
forum: Absolute Beginner Talk
---

### Post by Xephrey on 2007-04-29
Hey ya'll!  I recently ran these commands:


apt-get remove xserver-xorg
apt-get install xserver-xfree86


in hopes to fix some X server issues, which originally stemmed from having to change my resolution each and every time I logged in.  Well, Ubuntu doesnt boot anymore.  How do I undo this?  I guess having to change resolution every time is better than not booting at all... *sigh* I'm kind of tired of re-installing Ubuntu. It was fun at first, but I'm almost ready to resign to windows. 

Thanks!

-Xephrey

---

### Post by solar george on 2007-04-29
Try reinstalling xserver-xorg you can try booting into failsafe if you don't get as far as a command prompt in normal boot.

---

### Post by Seisen on 2007-04-29
To reinstall X-server do this in the terminal

```
sudo apt-get install x-windows-system-core
```

---

