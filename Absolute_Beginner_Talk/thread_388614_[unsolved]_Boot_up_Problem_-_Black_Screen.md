---
title: "[unsolved] Boot up Problem - Black Screen"
date: 2007-03-19
forum: Absolute Beginner Talk
---

### Post by Jenny201 on 2007-03-19
hello there,

I tried installation using live desktop but failed since I was getting a black screen. I then used alternate cd to install. I install everything.

Now I try to boot the ubuntu on my computer, but I get a black screen right before it is about to load the login screen. 

There is a small cursor frozen at top and that's about it. CTRL/alt/f1-f2-f3 or any other keys do not work! 

My spec:

Intel Pentium III Processor
697 MHz, 384 MB of Ram.
Graphic Card: Nividia Geforce MX 440.
LCD DELL MONITOR 17 Inchl <-- maybe that's the problem? I don't know.

Specs of monitor:

Here are the full specs of my monitor:



* Max resolution
1280 x 1024

* Dot pitch
0.264 mm

* Image brightness
250

* Display (projector) image contrast ratio
450:1

* Max vertical view angle
120

* Max horizontal view angle
140

* Max sync rate (V x H)
75 Hz x 80 KHz

* Analog video signal
---- RGB


THANKS! :)

---

### Post by teaker1s on 2007-03-19
boot recovery kernel
```
sudo dpkg-reconfigure xserver-xorg
```
you will need to know monitor technical specs ie horizontal /vertical and display resolutions
firstly try "nvidia" open gl driver if that won't work try "nv" and falling that try "vesa" as driver.

Also if this doesn't fix it there are others claiming flashing square and blank screen-worth reading those threads for any other ideas

---

### Post by Jenny201 on 2007-03-19
Hi, my monitor's resolution is 720x400 69Hz --- Optimum 1280x1024 60Hz.

---

### Post by Jenny201 on 2007-03-19
Here are the full specs of my monitor:



    * Max resolution
     1280 x 1024

    * Dot pitch
     0.264 mm

    * Image brightness
     250

    * Display (projector) image contrast ratio
     450:1

    * Max vertical view angle
     120

    * Max horizontal view angle
     140

    * Max sync rate (V x H)
    75 Hz x 80 KHz

    * Analog video signal
       ---- RGB 


What do you recommend?

---

### Post by teaker1s on 2007-03-19
as above the command I posted will allow you to configure linux to your display-I believe most of your issue is likely to be that ubuntu hasn't correctly set up with your display

---

