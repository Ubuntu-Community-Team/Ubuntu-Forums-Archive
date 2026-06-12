---
title: "restart x"
date: 2008-03-25
forum: Absolute Beginner Talk
---

### Post by rsarvi on 2008-03-25
I have read some instructions relating to changing the screen resolution in Xorg.conf and after doing that i need to "Restart X".. what is that "restart x"? Do i need to reboot completely?

Else how should I do it? Can i close that Xorg.conf file after saving? Or should I be in that screen to do that "restart x"? 

if there is a command to do in terminal, pls tell the cmd.


thanks in advance.

---

### Post by apothecaryaaron on 2008-03-25
One of the easier ways to Restart X is to hit "Ctrl + Alt + Backspace" to logout and then log back in.
 
If you prefer the mouse you can log out the clickety way as well.

---

### Post by wormser on 2008-03-25
Just close all your windows and press Ctrl + Alt + Backspace.  It's just a key combo.

---

### Post by aysiu on 2008-03-25
Control-Alt-Backspace is the quickest way.

You can also do Control-Alt-F1, log in, and type ```
sudo /etc/init.d/gdm restart
``` if you're using Ubuntu or Xubuntu, or type ```
sudo /etc/init.d/kdm restart
``` if you're using Kubuntu.

A reboot will work as well but take longer.

---

### Post by Paqman on 2008-03-25
> **rsarvi said:**
> what is that "restart x"?

X is the [X Server](http://en.wikipedia.org/wiki/X_server). It's the system that creates the graphical interface.

---

### Post by rsarvi on 2008-03-25
thx guys..

i will get back to u after trying it out

---

