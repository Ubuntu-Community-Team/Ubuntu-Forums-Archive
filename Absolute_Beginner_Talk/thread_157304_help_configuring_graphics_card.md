---
title: "help configuring graphics card"
date: 2006-04-08
forum: Absolute Beginner Talk
---

### Post by malavar on 2006-04-08
hey i just installed ubuntu breezy on a harddisk, and swapped that harddisk into a pc  that doesnt have cdrom or floppy disk. im having problems configuring the xserver now though. its a Hp DB670AV and i think the chipset is Intel 865-G Integrated Graphics. thanks!

---

### Post by taurus on 2006-04-08
You can configure your X again with this command from a terminal, Applications -> Accessories -> Terminal.
```

sudo dpkg-reconfigure xserver-xorg

```
I am sure you have to use "i810" as a driver for your Intel 865-G Integrated Graphics...

---

### Post by malavar on 2006-04-08
hey i reconfigured it and it started up for a second then crashed and gave me this

skipping
"/usr/X11R6/lib/modules/extensions/libGLcore.a:m_debug_clip.o": No symbols found
"/usr/X11R6/lib/modules/extensions/libGLcore.a:m_debug_norm.o": No symbols found

"/usr/X11R6/lib/modules/extensions/libGLcore.a:m_debug_xform.o": No symbols found

(EE) no devices detected

---

### Post by malavar on 2006-04-08
hey thanks for your help taurus i fixed the problem.

---

### Post by taurus on 2006-04-08
[QUOTE=malavar]hey thanks for your help taurus i fixed the problem.[/QUOTE]
You're welcome and by the way, how did you fix your problem so in case others know how to do it when they run into the same problem as yours?

---

### Post by malavar on 2006-04-08
sudo dpkg-reconfigure xserver-xorg , i left the Bus ID blank (good or bad idea?)  , and for server modules, i left out GLcore module (only because i noticed that was in the error message). it works for me.

---

### Post by taurus on 2006-04-08
[QUOTE=malavar]sudo dpkg-reconfigure xserver-xorg , i left the Bus ID blank (good or bad idea?)  , and for server modules, i left out GLcore module (only because i noticed that was in the error message). it works for me.[/QUOTE]
I never have Bus ID in my /etc/X11/xorg.conf anyway.  And for GLcore module, you can also comment it out in your /etc/X11/xorg.conf by placing a # in front of it!  ;)

---

