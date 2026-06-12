---
title: "xerox xk50cx"
date: 2006-12-12
forum: Absolute Beginner Talk
---

### Post by dbbolton on 2006-12-12
i'm trying to install a Xerox Workcentre XK50CX on xubuntu 6.06 (i also installed the ubuntu-desktop package, gnome-cups-manager, and so on)

the computer detects the printer and gcm recommends the lex5700 driver (the xk50cx isn't on the list; it selects this driver for a xk35c)

however, linuxprinting.org states:

> **Section 3: Xerox WorkCenter XK50cx**

        
3.1 _How do I set it up?_ Setting it up as a Lexmark GDI inkprinter with Ghostscript "stp" driver. gs -DIVICE=stp -sMODEL=lexmark-z52 
       3.2 _How well are the options supported?_ All resolutions and quality parameter are available. It is important to use the Lexmark Z52 model. Other models aren't compatible to higher resolutions ober 600x600i added a new printer as a lexmark z52 with the gutenprint driver, and under "connection" i chose "use another printer by specifying port", which is usb #1.

neither of these worked. with the lex5700 driver, the printer makes noises like it's printing but ultimately shoots out a blank page. with the gutenprint driver, it just spits out a blank page.

what exactly is "gs -DIVICE=stp -sMODEL=lexmark-z52"? when i run it in a terminal as sudo or not, i get this error:

-dvar=name requires name=null, true, or false


i read a bit on gs, and it seems to me that this command should be:
```
gs -sDEVICE=stp -sDeviceModel=lexmark-z52
```but, that gice the error: "unknown device: stp"

this is my friend's computer, so it really doesn't matter to me. but i would certainly like to help him and we would both appreciate your help.

---

### Post by dbbolton on 2006-12-12
please.

---

### Post by taurus on 2006-12-12
Please do not start the same thread while the other one is still active!!!

[http://www.ubuntuforums.org/showthread.php?t=317078](http://www.ubuntuforums.org/showthread.php?t=317078)

---

