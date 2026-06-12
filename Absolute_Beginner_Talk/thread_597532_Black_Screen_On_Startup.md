---
title: "Black Screen On Startup"
date: 2007-10-30
forum: Absolute Beginner Talk
---

### Post by thedrizz on 2007-10-30
Hiya,

So until yesterday whenever i booted ubuntu, it'd have the bar,  load, the screen would turn brown and i'd get my mouse for about 10 seconds, and i'd login. 

So i tried playing open arena yesterday, and my screen turned totally black. Its on, but its black. 

So i turned it off and went to bed. Today, when i try to boot, i get the bar, than the screen just turns black. I'm going to try and leave it on longer, but i waited like 5 minutes last time, and thats a LOT more than before.

Any idears? Oh and if its any help, i installed the ATI drivers for my Radeon 9800 video card yesterday, but the restart didnt screw it up like this before.....


Thanks in advance!

Edit: i think it may be the driver. Can i somehow reser it thru the recovery console? and if so, is there an alternative to he fglrx driver that runs compi?

---

### Post by Pumalite on 2007-10-30
You might have to configure xserver to get in the system
sudo dpkg-reconfigure xserver-xorg, use -vesa-.

---

### Post by EXCiD3 on 2007-10-30
I dont know about installing the graphics driver over agian but in console you can edit your xorg.conf to use the vesa driver.

```
sudo nano /etc/X11/xorg.conf
``` Look for your graphics card section and change the Driver "<driver name>" section to Driver "vesa". Save by pressing Ctrl-X and then type ```
startx
``` in console to start the xserver again. This should start the X server and at least make it usable. You may want to try reinstalling the graphics driver if you think that is the problem.

---

