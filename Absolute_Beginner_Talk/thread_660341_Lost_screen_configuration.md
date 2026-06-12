---
title: "Lost screen configuration"
date: 2008-01-06
forum: Absolute Beginner Talk
---

### Post by Coppper on 2008-01-06
Hi , 
I can only use a 640x 480 screen configuration, and till yesterday i had 1280 x 800 . 

Any idea why

---

### Post by eapache on 2008-01-06
Have you tried changing it under the Preferences menu?

---

### Post by Dr Small on 2008-01-06
What did you do to ruin your screen resolution? :p
Have you tried reconfiguring Xorg ?

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

---

### Post by Coppper on 2008-01-06
First , that resolution is the only one i get , so i cannot change it 

And that's the error i get when i type 
sudo dpkg-reconfigure -phigh xserver-xorg

xserver-xorg postinst warning: overwriting possibly-customised configuration
   file; backup in /etc/X11/xorg.conf.20080107000108

---

### Post by PlanetaryNapkin on 2008-01-06
I'm experiencing the same problem, in this instance after re-installing Ubuntu. Nothing but hideous 640 resolution, where once all was beautiful.

Got the exact same result spat back from the terminal for trying to reconfigure Xorg.

---

### Post by Coppper on 2008-01-06
I think i have fixed it ,  enabling the private device for my ATI card, but now i get a message saying 
that i'm using a private one .. is this normal ??

---

### Post by PlanetaryNapkin on 2008-01-06
It would be much appreciated if you posted the commands/actions for me.

---

### Post by PlanetaryNapkin on 2008-01-06
Seems the command works if you remove the '-phigh'.

Huzzah!

---

### Post by Coppper on 2008-01-06
OK , i'll try . My ubuntu is in spanish ... 
 System -> administration --> private drivers manager (or something  like that, sorry ) 
It pops up a window , chech the correct option . In my case it automatically  download and install 
the driver , then boot and voila !!! 

Hope it helps you

---

