---
title: "Laptop External Monitor"
date: 2007-03-31
forum: Absolute Beginner Talk
---

### Post by skobe on 2007-03-31
I want to run Ubuntu 6.10 on my Averitec 3200 series laptop.  I tried running it from the cd and I think everything works as it should except for my external screen.  I am using a ViewSonic screen and I would like to turn off my laptop screen and just use the external one.  When I first started Ubuntu both screens worked (except that the resolution was wrong for the external screen).  When I tried to turn off my laptop screen the external screen displayed a jumbled image that I could not make out.  When I tried to switch back, both screens displayed this image.  

Can anyone help?

---

### Post by annda on 2007-03-31
how do you turn off your laptop screen?

and most importantly, what video card do you have? have you installed the drivers?

---

### Post by skobe on 2007-03-31
I turn off my laptop screen using Function F5.  This toggles between using both monitors at the same time or either one individually.

I have a VIA/SG3 UniChrome Graphics video card.  (Does that sound right?)

I am running Ubuntu off of a CD; in Windows I have the drivers installed.  Do I need to install different ones for Ubuntu, or are they the same.

I am really new to this.  Thanks for your help.

---

### Post by annda on 2007-03-31
it seems like your displays have different resolutions and/or maybe different refresh rates, that's why you get a jumbled screen.

without installing ubuntu and linux via drivers (windows drivers are for windows only), along with an extension called xinerama, you will not be able to set separate resolutions and refresh rates for your displays.

i would suggest you find a resolution and refresh rate that both your displays like. then you will be able to switch screens without problems.

i specifically asked about the video card because i overlooked the fact that you run the live cd.

UPDATE: in case you decide to install in the future, this may be of some interest to you:
[http://www.hombrepac.com.ar/articulos/how-to-via-k8m890-chrome-9-igp-and-linuxs-xorg-ubuntu-edgy-610/](http://www.hombrepac.com.ar/articulos/how-to-via-k8m890-chrome-9-igp-and-linuxs-xorg-ubuntu-edgy-610/)

---

### Post by skobe on 2007-03-31
I read about xinerama somewhere else and I'll try it, but I don't quite understand "winthout installing ubuntu and linux via drivers".  Do I need to install ubuntu first? (Rather than run it off the CD)  Where can I find these drivers?

I'll check that link out.
Thanks again.

---

### Post by annda on 2007-03-31
i think any changes you do to your system whan running off a live cd are lost after reboot. so for example if you install a driver or a program, it works but when you reboot and go live again, the OS starts with a clean state and you have to install  again - every time.

as for the driver: anything can be found in synaptic: system > administration > synaptic

search for 'via xorg'. it should be xserver-xorg-video-unichrome

---

### Post by skobe on 2007-03-31
I'll try that; thanks.

---

