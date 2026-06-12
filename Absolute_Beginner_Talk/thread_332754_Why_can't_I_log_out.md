---
title: "Why can't I log out?"
date: 2007-01-06
forum: Absolute Beginner Talk
---

### Post by chris90uk on 2007-01-06
Hi,

When I log out of Ubuntu, the computer freezes just before it reaches the log in screen. The screen goes white and the mouse cursor freezes, so I have to turn off my computer at the button. This is on Edgy, but it also happened on Dapper. All I can do is shut down to log in again, but why do I have to :(?

Every time I install Ubuntu, SOMETHING different but important goes wrong, times like this make Windows seem more of an option. 

Cheers.

---

### Post by taurus on 2007-01-06
The spec of your machine would be nice...

---

### Post by rbhigday on 2007-01-06
If it happen on both version, it looks like the problem is your machine and not the software.

---

### Post by chris90uk on 2007-01-06
> **taurus said:**
> The spec of your machine would be nice...

It is a laptop with 512 mb ram a AMD Sempron 1.7ghz processor (about that anyway) and an ATI Radeon xpress 200m graphics card. 

Any help to you>

---

### Post by riven0 on 2007-01-06
Does the same thing happen when you hit CTRL + ALT + Backspace? 

... just trying to determine whether it's the xserver, gnome or something else...

---

### Post by chris90uk on 2007-01-06
> **riven0 said:**
> Does the same thing happen when you hit CTRL + ALT + Backspace? 

... just trying to determine whether it's the xserver, gnome or something else...

I can log out fine with that combination, what makes it different?

---

### Post by riven0 on 2007-01-06
CTRL + ALT + Backspace tells the xserver to forcefully restart, so it's like doing a complete restart as far as the graphical display goes. Since that went fine we can rule out the xserver as being the cause of the problem, which is good - there are many DE's but only one xserver. :p 

Maybe it's something wrong with gdm. Is something mis-configured? Why don't you try re-installing it, too?:

> sudo dpkg --configure -a && sudo apt-get install --reinstall gdm

See if you get any errors, then try to log out. If you get stuck again, just do another CTRL + ALT + Backspace

---

