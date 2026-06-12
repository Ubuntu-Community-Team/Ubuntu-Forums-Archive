---
title: "resolution problems"
date: 2006-10-01
forum: Absolute Beginner Talk
---

### Post by cmaranhao on 2006-10-01
i edited my resolution in two different ways:

nano and gedit.. i want the resolution to be at 1280x1024 but i cannot change it in the preferences > screen resolution menu because it only goes to 800x600.. i cannot change the refresh rates either.

any tips?

---

### Post by bulldog on 2006-10-01
Install drivers for your graphics card would do.

What resolutions are supported by your monitor?

---

### Post by captainroin on 2006-10-01
dont know if you tried this already but i had to add a modline

heres the tool: [http://www.dkfz-heidelberg.de/spec/linux/modeline/](http://www.dkfz-heidelberg.de/spec/linux/modeline/)

and search for modline in the forums and you'll find how to add.

hope that helps.

---

### Post by NESFreak on 2006-10-01
```
sudo dpkg-reconfigure xserver-xorg
``` gives you a guided setup of xorg.

NESFreak

---

### Post by cmaranhao on 2006-10-01
> **bulldog said:**
> Install drivers for your graphics card would do.

What resolutions are supported by your monitor?

the monitor can go to 1280x1024 with no problems.. it is a samsung syncmaster 710n.

---

### Post by cmaranhao on 2006-10-01
> **NESFreak said:**
> ```
sudo dpkg-reconfigure xserver-xorg
``` gives you a guided setup of xorg.

NESFreak

i already tried that but it asks me stuff i don't know how to answer.. i need another way to set the resolution

---

### Post by bulldog on 2006-10-01
Install the driver for your graphic's :D 

Maybe I should take my bycicle and come over to you and do it myself?](*,)

---

### Post by bigken on 2006-10-01
> **cmaranhao said:**
> i already tried that but it asks me stuff i don't know how to answer.. i need another way to set the resolution


Just select your video driver and resolutions just hit enter for the rest ;)

---

### Post by cmaranhao on 2006-10-01
> **bulldog said:**
> Install the driver for your graphic's :D 

Maybe I should take my bycicle and come over to you and do it myself?](*,)

my graphics card is a nvidia 6800gt.. i searched nvidia site for linux drivers and i came up with this:

[http://www.nvidia.com/page/partner_certified_drivers.html](http://www.nvidia.com/page/partner_certified_drivers.html)

---

### Post by NESFreak on 2006-10-01
just install them with ```
sudo aptitude install nvidia-glx
```
restart and run ```
sudo dpkg-reconfigure xserver-xorg
``` select nvidia in place of nv, select the glx module. restart X (ctrl alt bckspace)

or check this [wiki]("https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia")

NESFreak

---

### Post by cmaranhao on 2006-10-01
> **NESFreak said:**
> ```
sudo dpkg-reconfigure xserver-xorg
``` gives you a guided setup of xorg.

NESFreak

done it, the resolution hasn't changed and i have this message:

xserver-xorg postinst warning: overwriting possibly-customised configuration
   file; backup in /etc/X11/xorg.conf.20061001191132

---

### Post by bulldog on 2006-10-01
@TS can you explain to me what this means?

xserver-xorg postinst warning: overwriting possibly-customised configuration
file; backup in /etc/X11/xorg.conf.20061001191132

---

### Post by cmaranhao on 2006-10-01
> **NESFreak said:**
> just install them with ```
sudo aptitude install nvidia-glx
```
restart and run ```
sudo dpkg-reconfigure xserver-xorg
``` select nvidia in place of nv, select the glx module. restart X (ctrl alt bckspace)

or check this [wiki]("https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia")

NESFreak

done all that, resolution went from 800x600 to 1024x768.. not quite the desired 1280x1024 :(

---

### Post by bigken on 2006-10-01
> **cmaranhao said:**
> done all that, resolution went from 800x600 to 1024x768.. not quite the desired 1280x1024 :(

using the dpkg command again manually select the 1280x1024 ;)

---

### Post by cmaranhao on 2006-10-01
nice, i have 1280x1024 screen resolution :mrgreen: 

many thanks guys, linux community is very newbie friendly 8)

---

### Post by bigken on 2006-10-01
very happy for you enjoy ubuntu :D

---

