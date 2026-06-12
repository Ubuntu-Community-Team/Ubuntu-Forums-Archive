---
title: "desktop colour depth"
date: 2006-04-09
forum: Absolute Beginner Talk
---

### Post by tracewalk on 2006-04-09
This might sound like a silly question from one who has migrated from Windows.. but..  A game (Imogen from ovine.net) I downloaded seems to have installed via wine but when I try to open the .exe file a message box asks me to change to 16bit or 32 bit colour depth.  Is there a simple way of doing this?:confused: 
Moz

---

### Post by slipk487 on 2006-04-09
you cant get ubuntu to go to 32 bit but run
```
sudo dpkg-reconfigure xserver-xorg
```
and select 16 bit but dont change anything else

---

### Post by sYs^ on 2006-04-09
Or you can open /etc/X11/xorg.conf and change the *DefaultDepth * option in the *Screen* section.

---

### Post by tracewalk on 2006-04-10
Thanks slipk487!  Up and running perfectly.
Moz

---

### Post by slipk487 on 2006-04-10
your welcome

---

