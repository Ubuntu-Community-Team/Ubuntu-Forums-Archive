---
title: "screenshots"
date: 2008-01-08
forum: Absolute Beginner Talk
---

### Post by Shirobon on 2008-01-08
Hi,

Is it possible to do a screenshot while i'm installing Ubuntu server 7.10 . I  want to use them to make a documentation.

---

### Post by koshari on 2008-01-08
the best way to do this it to install ubunto using a virtual machine, then you can use all the goodies like printScreen and recordmydesktop to make top notch tutorials, works for windows and any other OS you install as a virtual machine.

---

### Post by Shirobon on 2008-01-08
did raid work with virtual machine?
I want to install my hard drives in raid. (sorry for my poor English).

---

### Post by geirha on 2008-01-08
To take a screenshot of the entire desktop, hit the Print Screen button on your keyboard.
To take a screenshot of the currently active window, hit Alt+Print Screen

Make sure you save them to a harddrive, they'll be written to the Desktop by default, which will be lost when you reboot

EDIT: Oops, didn't notice it was Ubuntu **server**, sorry.

---

### Post by kellemes on 2008-01-08
> **Shirobon said:**
> Hi,

Is it possible to do a screenshot while i'm installing Ubuntu server 7.10 . I  want to use them to make a documentation.

Don't you have a digital camera you can use? This is the easiest way to create shots during a install.

---

### Post by Shirobon on 2008-01-08
well it's possible to do this at the last resort

---

### Post by (((X))) on 2008-01-08
code:
xwd -root -out screenshot.xwd

screenshot will be placed in your homedir

---

### Post by Shirobon on 2008-01-09
-sh: xwd: not found

well it doesn't seem to work since there's no OS installed.

---

### Post by (((X))) on 2008-01-10
ow, sorry

---

### Post by geirha on 2008-01-16
I came across [this](http://p12n.org/hacks/) recently and remembered this thread. The ubuntu server install is curses based right? so the screendump-script at that site might be just what you're looking for. Download it during install, and run "screendump 1 >dumpX.txt" whenever you want to take a screenshot, then in a gui, open a terminal and type "cat dumpX.txt" and it should look like what you saw in the installer.

---

