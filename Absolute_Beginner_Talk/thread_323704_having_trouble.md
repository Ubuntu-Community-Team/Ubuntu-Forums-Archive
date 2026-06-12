---
title: "having trouble"
date: 2006-12-22
forum: Absolute Beginner Talk
---

### Post by ptgmc29 on 2006-12-22
ok i tried edgy live cd on my laptop and decided to install it on my desktop. the only issue is my video card isnt displaying anything once everything is loaded. i can hear the chime but get an out of range signal. ive tried changing resolutions and changing settings on the monitor itself but nothing works.i dont know what else to do. ive searched but havent found the answer. how do i update the driver if i cant see anything?

this is for a nvidia geforce mx 440

i have no experience with this. 

please help!

---

### Post by meng on 2006-12-22
Is yours an LCD monitor? I wonder if it's a refresh-rate problem, i.e. the video card is sending an unacceptable refresh rate frequency.

---

### Post by ptgmc29 on 2006-12-22
yes it is. how would i change it or what does it need to be? as far as i can tell its at 60htz now

---

### Post by meng on 2006-12-22
If you want to try the OS before you install it, then boot into safe graphics mode. Or else, if you already know that you want to install it anyway, you could download and burn the Alternate CD, which has a text-based installer. Either way you'll most likely need to do some minor reconfiguration post-install.

---

### Post by Rescue Penguin on 2006-12-22
I think meng has a point, have you tried a generic driver for your monitor type? I would try a generic driver at a low resolution first.

                                      Steve

---

### Post by ptgmc29 on 2006-12-22
ive tried safe graphics mode and the lowest resolution. neither helps. i will try the alternate cd.

---

### Post by meng on 2006-12-22
When the chime sounds, but your monitor is black, also try:
ctrl-alt-f1
to see if you get dropped to a console. (That will be important for later, when you may need to reconfigure your xserver from a console.)

---

### Post by ptgmc29 on 2006-12-23
> **meng said:**
> When the chime sounds, but your monitor is black, also try:
ctrl-alt-f1
to see if you get dropped to a console. (That will be important for later, when you may need to reconfigure your xserver from a console.)
yes that works. so then i install the nvidia-glx or at least i think so, then what do i do? if i reboot it does nothing.  im only on live cd mode. i have yet to burn the alternate cd. i am going to do that now...

---

### Post by meng on 2006-12-23
The liveCD isn't going to allow permanent changes, once you reboot you start from scratch again. Burn the alternate CD, install and then we'll talk! :D

---

