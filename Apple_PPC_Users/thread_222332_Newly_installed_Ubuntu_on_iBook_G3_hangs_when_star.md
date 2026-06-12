---
title: "Newly installed Ubuntu on iBook G3 hangs when starting X"
date: 2006-07-24
forum: Apple PPC Users
---

### Post by shortyzgotpop on 2006-07-24
I got this old iBook G3, 800 Mhz, 128 MB ram from a friend of mine, and I promptly installed Ubuntu-powerpc. That went smoothly. I boot it up it shows "Ubuntu" and underneath all the modules its loading, but right after that when it's starting gnome/x the screen completely goes grey with tiny grey lines scrolling up and down the screen. I'm trying to get to a console view to do a "dpkg-reconfigure xserver-xorg" but when I hit Alt+Option+F2 the screen just changes color and looks wierder. Can anybody please tell me how to fix this problem? And one other thing, I can't eject the CD drive at all. Is there a manual way to do it instead of apple's dedicated key? Thank you!

---

### Post by shortyzgotpop on 2006-07-24
I've also tried hitting Alt+Opt+F1, that had pretty much the same effect as F2, with the screen becoming a rainbow. And before you ask, I've used the boot option video=ifonly and I still encounter the problem. What I mainly believe I need help in doing is getting to see a console and doing a reconfigure of xserver. I think that would fix it. Thanks!

---

### Post by shortyzgotpop on 2006-07-25
Ok I've discovered the boot option 'Linux single' takes you straight to the console. Hopefully this will allow me to reconfigure xserver and fix the problems.

---

### Post by chasisaac on 2006-07-28
> **shortyzgotpop said:**
> Ok I've discovered the boot option 'Linux single' takes you straight to the console. Hopefully this will allow me to reconfigure xserver and fix the problems.

Bummer, sorry noone else answered your question. Did you get it working?

---

### Post by liam_stoush on 2006-07-28
I can't help with the x configuration, but if your iBook is one of the older models and has a tray drive, there's a millimetre-wide hole in the face of the tray into which you can insert a straightened paperclip, pin or pencil lead to manually eject the CD.
If it's a slot-loading iBook, there's always the solution of holding in the trackpad button (or left mouse button) while booting, which should also eject the CD.

---

### Post by 3rdalbum on 2006-07-28
It's video=ofonly, not video=ifonly ;-)

---

### Post by shortyzgotpop on 2006-07-29
Yes guys thank you I managed to get it working. Turns out the system didn't think there was any monitor attached to it (in this case the LCD). I added Option "MonitorLayout" "LVDS" to the graphics section of xorg.conf and it fixed it!

---

