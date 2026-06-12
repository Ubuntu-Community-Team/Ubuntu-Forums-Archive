---
title: "External Monitor Resolution MacBook 5.1 Intrepid"
date: 2008-12-14
forum: Apple Hardware Users
---

### Post by Heleen on 2008-12-14
Hello,

I've just managed to install Ubuntu Intrepid Ibex on my MacBook. Now obviously there are a lot of problems still to overcome, but there's one problem specifically that I would really like to be solved, because I'm going to have to do a lot of programming in Linux the next couple of weeks on my laptop.
I have an external monitor (Dell 24 inch) that I hook up to my laptop.
Now I've installed the Nvidia restricted drivers (177.80), and it can do TwinView using the Nvidia X server settings, but it doesn't get the resolution right on the external monitor.
It detects the display correctly and it says that the native resolution is 1920x1200, but when I want to set the resolution in the Display configuration the highest possible resolution is 1152x864. I have not set it to be the primary display for the X screen.

Does anyone know how I can solve this problem? I have downloaded the newest driver off the Nvidia website (177.82) but haven't tried to install it yet (it's an rpm as well).
I would be very grateful if someone could help me.
Thanks!
Heleen

---

### Post by carrick on 2009-01-05
I am also having this problem.  Any advice would be great.

---

### Post by olavjunior on 2009-01-15
What? (Sorry for being off topic) Have you gotten the mini-display-port to work? When I connect an external monitor nothing shows up in xrandr og nvidia. That's why I'm stuck with OSX for the moment

---

### Post by copyrights on 2009-01-26
It seems to be that you have to edit the /etc/X11/xorg.conf

here the lines form my xorg.conf (resolution of external screen 1650x1050)

```

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "1"
    Option         "TwinViewXineramaInfoOrder" "DFP-0"
    Option         "metamodes" "DFP-0: nvidia-auto-select +1680+505, DFP-1: 1680x1050 +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

```

It's configure to detect macbook screen automatically (nvidia-auto-select) with the position +1680+505 and my external screen with 1650x1050 at +0+0

---

