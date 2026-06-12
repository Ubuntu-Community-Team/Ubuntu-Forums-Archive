---
title: "Forward and back mouse buttons on Firefox."
date: 2007-07-03
forum: Absolute Beginner Talk
---

### Post by jerrynewt on 2007-07-03
Just installed Fiesty on my Gateway GT5012 Media Center comp and so far most everything is doing fine with only a few minor problems. Trying to get the Ubuntu Forums add on from Firefox to be added to my toolbar and can't seem to remember how I did it on my other comp about two months ago. I downloaded and installed the add on just fine but can't remember how to enable it so it will show up in the toolbar. Any help is appreciated.

---

### Post by jerrynewt on 2007-07-03
Sorry--left out the part about getting the forward and back buttons on my mouse to work also. I have a Microsoft Wireless Laser Mouse 6000. Thanks again.

---

### Post by hyperq on 2008-02-06
I got the side mouse buttons on my Logitech MX518 working in Firefox.  I am using the "evdev" driver, not the "mouse" driver.  I am using Kubuntu 7.10 Gutsy, which already has the package "xserver-xorg-input-evdev" installed by default.

Simply change the mouse section of your /etc/X11/xorg.conf to this: 

[HTML]
Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "evdev"
        Option          "CorePointer"
        Option          "Buttons"       "7"
        Option          "ZAxisMapping"  "4 5"
        Option          "ButtonMapping" "1 2 3 6 7"
        Option          "Name"  "Logitech USB-PS/2 Optical Mouse"
EndSection
[/HTML]

---

### Post by jjnguy13 on 2008-02-07
I did what you said to try to fix the same problem.

After I restarted GNOME it came back in low graphics mode.

So, I wouldn't try the above suggestion if I were you.

---

