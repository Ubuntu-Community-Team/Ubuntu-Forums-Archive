---
title: "Change Resolution"
date: 2007-01-14
forum: Absolute Beginner Talk
---

### Post by Sir_Sid on 2007-01-14
Im running Ubuntu on a good pc, but with a 10 year old crt monitor. It only supports 800X600. Where do I change the resolution to that. Its running on a higher one right now and small edges of the screen are extending off the edge of the screen.

---

### Post by aysiu on 2007-01-14
Log out of Gnome (or KDE or XFCE)

Press Control-Alt-F1

Log in

Type ```
sudo dpkg-reconfigure xserver-xorg
``` Answer the questions as best you can. Otherwise, go with the defaults. When you get to the part about screen resolutions, press Space Bar on 800x600

When you're done, press Control-Alt-F7 and then Control-Alt-Backspace

Log in again and hopefully 800x600 should show up as an available resolution.

---

### Post by smoker on 2007-01-14
go to system, preferences, and choose 'screen resolution' and change there,

---

### Post by MkfIbK7a on 2007-01-14
are you sure the screen isnt streched if it is a tube display you should be able to adjust that if not
go
 system>preferences>display
i think i havent used gnome in a long time....
if not you can do 
sudo dpkg-reconfigure xserver-xorg
and when it asks about resolution use space to choose 860x600

**EDIT: aysiu beat me to it**

---

