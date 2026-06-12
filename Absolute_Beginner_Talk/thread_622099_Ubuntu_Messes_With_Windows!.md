---
title: "Ubuntu Messes With Windows!?"
date: 2007-11-24
forum: Absolute Beginner Talk
---

### Post by kevin11951 on 2007-11-24
i booted ubuntu off the live cd (ubuntu 7.10 64bit). i didnt do anything besides boot it, run sudo dpkg-reconfigure xserver-xorg (to fix the refresh rate problems), logged out, and back in, (keep in mind ubuntu was NOT installed on the hdd), i then restarted back into windows, and windows gave me every error under the sun (it didnt kill anything, all my files and programs were there, just every error under the sun). 

would just doing that, do something to windows, and/or the hardware windows runs on? if it matters, when i chose the driver for ubuntu to use for the nvidia video card, i chose vesa.

---

### Post by arsenic23 on 2007-11-24
Can you be more specific about the errors?

Where you getting crash handler errors, GPFs, IRQnotlessthenequal.., or... ?

---

### Post by jingo811 on 2007-11-24
Usually no but then I've never tried Gutsy 7.10 LiveCD so I wouldn't know for sure.  But are you saying that your PC only have Windows or does it have a Dualboot Windows/Ubuntu option at this point?

---

### Post by kevin11951 on 2007-11-24
the error in question was one i have never gotten before... when windows started up it brought me to a window saying "windows could not startup". and spent an hour doing something to itself... and also it wanted to restore. i canceled out of the restore, and then finally in rebooted and all was well... the point is, i have never had a live cd do anything, i just wanted to know if it was common, or if i was the exception.

---

### Post by kevin11951 on 2007-11-24
and yes... only windows

---

### Post by arsenic23 on 2007-11-24
Is it possible that instead of shutting down windows before booting the live cd, that you instead used Windows' hibernate feature?  I -think- that something like that could cause a one time cosmetic error, but I'd have to go install windows on something and try it myself to be sure.

---

### Post by kevin11951 on 2007-11-24
> **arsenic23 said:**
> Is it possible that instead of shutting down windows before booting the live cd, that you instead used Windows' hibernate feature?  I -think- that something like that could cause a one time cosmetic error, but I'd have to go install windows on something and try it myself to be sure.

i pushed restart (its vista) and it restarted, and then i missed the cd part, it got to the windows logo, and i hard booted, getting the cd that time 'round!

---

### Post by kelbizzle on 2007-11-24
> **kevin11951 said:**
> i pushed restart (its vista) and it restarted, and then i missed the cd part, it got to the windows logo, and i hard booted, getting the cd that time 'round!

If it started to load the os or mount the drives. And you just held the power button until it shutoff so you could quickly restart it. That may have been what caused the errors. Once it's already starting up it would be good to let it continue to start up before restarting it again.

---

### Post by Firestone on 2007-11-24
If I restart from Ubuntu to Windows it cant find my tv-card and gives a few driver errors. A cold boot directly to Windows doesnt cause the problem. I've tried to find out why a while ago, and iirc it was caused by data send through the bus by the OS you're in at that moment. A cold boot resets this, thus removing the problem.

---

