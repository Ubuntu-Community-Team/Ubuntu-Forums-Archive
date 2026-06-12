---
title: "NVidia driver"
date: 2007-02-05
forum: Absolute Beginner Talk
---

### Post by smallmouth sam on 2007-02-05
I am trying to enable nvidia driver for geforce 4 ti 4200
keep getting message

su nvidia ... enable =
Error: unable to load nvidia kernel driver! Be sure to have installed
the nvidia driver for your running kernel.

glxinfo ... =
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".

what am i doing wrong?

---

### Post by shareMenaPeace on 2007-02-05
Here is a beryl install guide - featureing nvidia driver install.
[http://doc.gwos.org/index.php/BerylOnEdgy](http://doc.gwos.org/index.php/BerylOnEdgy)

---

### Post by bodhi.zazen on 2007-02-05
IMO the easiest way of installing teh nvidia driver is with envy:

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

Although you can try:

```
sudo aptitude install nvidia-glx 
sudo aptitude upgrade
```

---

### Post by smallmouth sam on 2007-02-06
envy is is cool 

thank you alberto
:guitar:

---

### Post by CallsignBaron on 2007-02-07
I have the Nvidia GeForce4 Ti 4200 and envy installed the latest and correct driver from the Nvidia website. Excellent script, highly recommend it.

---

### Post by b1r469 on 2007-02-08
OMG envy was sooo easy. :)

Thank You for the link.

I've been searching for help in this category for weeks.  :)

---

### Post by neighborlee on 2007-02-10
> **b1r469 said:**
> OMG envy was sooo easy. :)

Thank You for the link.

I've been searching for help in this category for weeks.  :)

lets not give the impression it works for everyone..I treid it on my stock kernel, and it blanked out to a totally black screen, with underlying flashing cursor in upper left corner of screen and just hung there..and I have a  well known nvidia 6800  xt card..

cheers
nl

---

### Post by arochester on 2007-02-10
neighborlee

You should have tried Ctrl+Alt+F1

I've seen this flashing cursor too

It kind of hides and underlying that it's kind of asking you a question as well

It might work for you as well

---

### Post by ichan83 on 2007-02-12
hi,

i've been trying to install an nvidia driver after upgrading to edgy and am terribly unsuccessful. it all started when i tried to install beryl and could not enable the nvidia driver. so i tried to run the latest stable envy script and after installing it, all i see is a black screen!

i just changed the driver in xorg.conf from "nvidia" to "nv" and i can startx now but i get the same message that smallmouth sam gets.

i have a geforce 4 ti4200. do you guys have any suggestions? thanks

edit: i've tried using envy to uninstall the drivers and reinstall the drivers and now even when i change "nvidia" to "nv" in the .conf file i still get a blank screen
when i press alt-F1 to exit i get:
XIO: fatal IO error 104 (connection reset by peer) on X server ":0.0"
after 0 requests (0 known processed) with 0 events remaining.

any help is appreciated thanks

---

