---
title: "Display scaling &amp; Trackpad right mouse button"
date: 2020-11-26
forum: Apple Hardware Users
---

### Post by danblack2 on 2020-11-26
I've just installed Lubuntu 20.04 on my old ~2013 Macbook Pro. Overall I'm really impressed. It's a while since I've used Lubuntu apart from the network card everything pretty much worked out of the box. There are a couple of things I can't seem to find setting for, or help for online. Possibly because of the recent change to LXQt.

The main problem is that I can't find any options to scale the display.  Everything is pretty tiny on this 2560 x 1600 13" display. Is there a way to do this in Lubuntu 20.04. Or is there something I can install to achieve this. 

The other issue is livable with, as I can plug in a mouse, but it would be nice to be able to right click on the track pad. In OS X right click can be configured to work by two fingered click, or clicking the bottom right corner of the track pad, where the right button would be. Is there a way to enable this option in Lubuntu. Or again, does anyone know of a way to add support for this?

Thanks

[EDIT]  I tried setting the display to 1920 x 1200, which is better, but I was looking for smooth scaling of the display, between resolutions.

---

### Post by danblack2 on 2020-11-27
In case anyone else with a Mac is trying to get the trackpad working, the answer is yes and no. No you cant do this as default, but yes you can get the track pad working using other drivers. MTrack needs to be cloned, built and configured. I've not got my setting quite right yet, but it seems to work and be configurable. 
[https://github.com/p2rkw/xf86-input-mtrack](https://github.com/p2rkw/xf86-input-mtrack)

Regarding the display scaling, this is what I was asking about. It seems it is possible on Ubuntu 20.04 at least. 
[https://www.omgubuntu.co.uk/2020/04/ubuntu-20-04-fractional-scaling-support-setting](https://www.omgubuntu.co.uk/2020/04/ubuntu-20-04-fractional-scaling-support-setting)

Bonus question. Is there a way to set a default back-light brightness, or for previous back-light brightness settings to be restored at log in. Mine is reset to full brightness every time I log in.

---

### Post by Frogs Hair on 2020-11-27
Moved to ***Apple Hardware Users***.

---

### Post by sebadamus2 on 2020-12-23
Just to add, dont know if it helps you or others, but I had being using touchegg gestures daemon (installed from github deb package), that works with the libinput and my touchpad works almost like the real in osX.  4 finger swipe, 3 finger (2 fingers already worked)
Its a MBP 8.2 2011

---

