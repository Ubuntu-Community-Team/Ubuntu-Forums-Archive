---
title: "Revert To Generic Video Driver"
date: 2007-12-25
forum: Absolute Beginner Talk
---

### Post by Epic Plecostomus on 2007-12-25
Ok I'm posting from my desktop.  I let it talk me into using drivers for my nvida card.   Now I'm locked in 640x48 mode.   HELP!  How do I go back to whatever it was using upon install?  

Prob'ly one of amazing one-line SUDO terminal commands, right?  :biggrin:

---

### Post by taurus on 2007-12-25
```
sudo dpkg-reconfigure -phigh xserver-xorg
```

---

### Post by Epic Plecostomus on 2007-12-25
That got 'er.   *bow*

---

### Post by Chaositect on 2008-03-21
in a related issue, my newbsauce self has managed to change drivers to a non-working mode, and wonder if there's a pre-bootup safe mode...  or am I doomed to re-install?  I'm still figuring out the whole graphics window thing...

On my other computer I can't get dual monitors to work. (second is TV)  Wondering if there's a special fix for that.

Thanks for the help!

---

