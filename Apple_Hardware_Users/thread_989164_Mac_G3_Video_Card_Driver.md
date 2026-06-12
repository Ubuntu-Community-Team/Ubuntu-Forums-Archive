---
title: "Mac G3 Video Card Driver"
date: 2008-11-21
forum: Apple Hardware Users
---

### Post by ginbas on 2008-11-21
This is for anyone attempting to resurrect a mac g3 back to life with Hardy 8.04. 

What I have is a G3 B&W 400mhz with the original Rage128 16mb PCI video card. After fiddling and fooling with the "/etc/X11/xorg.conf" file I was able to get direct rendering enabled.

> user@powerG3:~$ glxgears
1728 frames in 5.0 seconds = 345.514 FPS
1828 frames in 5.0 seconds = 365.411 FPS
1824 frames in 5.0 seconds = 364.675 FPS

What really keeps this from working straight from install in that the default color depth is set at 24 where the card doesn't have enough video memory. So you need to force it to use 16 bit color in order to enble acceleration. 

I used the original Apple 17" Studio CRT and had to specify the values of that monitor in xorg.conf as well.

Here is my xorg.conf

```
Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "us"
        Option          "XkbOptions"    "lv3:lwin_switch"
EndSection

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
EndSection

Section "Device"
        Identifier      "Configured Video Device"
        BusID           "PCI:0:16:0"
        Option          "UseFBDev"              "true"
EndSection

Section "Monitor"
        Identifier      "Configured Monitor"
        Horizsync 25-80
        Vertrefresh 50-75
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
        DefaultDepth 16
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
EndSection

```

Compiz is not supported by this card however. Rage128's lack compositioning ability. I have however successfully played extremetuxracer!

---

### Post by lemonbar on 2008-11-22
Yay!  I'll have to try this.  Thanks for posting - I've been in G3 purgatory lately, and I have two other G3's waiting for conversion.

---

### Post by stream303 on 2008-11-22
You have THREE G3's?  Wow, no wonder I'm a bit confused. :)

Definitely keep these faqs handy if you haven't been to them already:

[https://wiki.ubuntu.com/PowerPCKnownIssues#Blank%20screen%20on%20iMac%20G3](https://wiki.ubuntu.com/PowerPCKnownIssues#Blank%20screen%20on%20iMac%20G3)

and

[https://wiki.ubuntu.com/PowerPCFAQ#3D%20video%20drivers,%20Beryl,%20Compiz](https://wiki.ubuntu.com/PowerPCFAQ#3D%20video%20drivers,%20Beryl,%20Compiz)

Although I'm not too big of a fan of trying to get 3D to run *well* on these boxes.

To avoid any frustration, be sure to check out exactly which models you have at:

[http://www.everymac.com/systems/apple/imac/index-imac.html](http://www.everymac.com/systems/apple/imac/index-imac.html)

And pay attention to the hard drive size limitations.  Most of the G3 iMacs have 8gb partitioning limitations for / (root), (some have 128gb limitations) so you'll have to do a custom partition if you have a replacement drive larger than the max listed as allowed.

Just wanted to let you know up front, so you don't try to throw them through the window. :)

---

### Post by lemonbar on 2008-11-22
Yep - one's a Graphite (my first computer ever), and the one I'm working on now was left by a dumpster at a friend's apartment (college town - people leave perfectly good electronics sitting next to dumpsters all over town at the end of semesters).  The other is one I'm gutting for parts, but I've amassed enough mac stuff to build an obsolete megarobot:)

I must've been really tired when I saw this - I don't think this is the answer to my problem.  I'll hop away now:)

---

