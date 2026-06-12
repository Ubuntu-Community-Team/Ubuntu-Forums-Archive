---
title: "Trying To Install Ubuntu With My ATI x800."
date: 2006-11-26
forum: Absolute Beginner Talk
---

### Post by mercera_13 on 2006-11-26
When I try to install ubuntu with my ATI x800 i get a error, Is this known with x800's or is it a problem with the interface as well should I try one of the ubuntu based distro's which use KDE?

---

### Post by junglepeanut on 2006-11-26
You need to give more information regarding your error. Is it a blank screen, is a a no screens found or something else?

---

### Post by redDEADresolve on 2006-11-26
> **junglepeanut said:**
> You need to give more information regarding your error. Is it a blank screen, is a a no screens found or something else?

Yes please list everything about your machine as well as any specific information about your error. Taking a screen shot would also be helpful. Just hit the print screen key on your keyboard.

---

### Post by unfun on 2006-11-26
In a terminal type

sudo apt-get install xorg-driver-fglrx
sudo aticonfig --initial
sudo aticonfig --overlay-type-Xv

and then either startx if you are in console
or Ctl+Alt+Backspace if in virtual terminal.

---

### Post by mercera_13 on 2006-11-26
Thanks A Lot For Your Help..

:D

---

