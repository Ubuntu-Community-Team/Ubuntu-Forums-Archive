---
title: "Quitting XWindows"
date: 2007-03-18
forum: Absolute Beginner Talk
---

### Post by jmattos on 2007-03-18
Hi there

how do I quit Xwindows to get to the command prompt? Then how do I get back into xwindows?

I tried ctrl-alt-F1 and I just get graphical noise, but no command prompt.

---

### Post by oilchangeguy on 2007-03-18
have you tried, applications, accessories, terminal?

---

### Post by jmattos on 2007-03-18
Yes, but I'm installing the ATI drivers so i need a true terminal session (for lack of a better term). from here.. [http://discoverx.wordpress.com/2007/03/12/a-fast-way-to-install-ati-and-nvidia-drivers-in-ubuntu/](http://discoverx.wordpress.com/2007/03/12/a-fast-way-to-install-ati-and-nvidia-drivers-in-ubuntu/)

---

### Post by jmattos on 2007-03-18
A thought... what if I just load using "recovery mode" at the GRUB prompt? would that do it?

---

### Post by jeffathehutt on 2007-03-18
Recovery mode should do it, but here is another way.

Close all open programs, then open a new terminal from the menu.  Type: 
```
sudo /etc/init.d/gdm stop
```
and it should drop you to a terminal.  To get back to X, type:
```
sudo /etc/init.d/gdm start
```

---

### Post by jmattos on 2007-03-18
Works like a champ. Thank you!

---

