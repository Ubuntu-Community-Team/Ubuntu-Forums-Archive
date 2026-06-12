---
title: "Debian Menu"
date: 2007-03-27
forum: Absolute Beginner Talk
---

### Post by J11Gyro on 2007-03-27
On my last install I had the Debian Menu working and the config, now for some reason it shows up but cannot configure it or use it  any ideas?

---

### Post by dreadlord_chris on 2007-03-27
```

sudo aptitude install menu

```
will get your Debian Menu back

---

### Post by J11Gyro on 2007-03-27
Got it, thank you for the help

---

### Post by kisiyel on 2007-03-27
> **dreadlord_chris said:**
> ```

sudo aptitude install menu

```
will get your Debian Menu back

I installed "menu", but still I can not see debian menu. I checked all the recommended packages are satisfied. Is there another package I have to install :confused:

---

### Post by kisiyel on 2007-03-28
Solved the problem by first installing "menu" then "menu-xdg" at different times. Strange but worked for me.

---

### Post by Subban on 2007-04-14
*** * Fixed with sudo update-menus -v**

I can't get this to work, installed both "menu" and "menu-xdg"
Menu didn't show up. Right Clicked "Application" menu, chose "Edit Menus". 
I could see the "Debian Menu" there disabled, tried enabling it, but it just disables itself.
Now its vanished all together :confused: 

Doing this on Feisty btw, anyone know whats gone wrong please ?

---

