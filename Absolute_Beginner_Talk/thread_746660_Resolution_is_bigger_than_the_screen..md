---
title: "Resolution is bigger than the screen."
date: 2008-04-05
forum: Absolute Beginner Talk
---

### Post by bsiebert on 2008-04-05
Hello,
      Im having a problem with my resolutions. First all I have a 22" Westinghouse and I know the native resolution is 1680x1050. I have the ATI graphics cards and they are working fine. The only problem is when I try to set my resolution to 1680x1050 its like the desktop just gets bigger and then I have to scroll to get to the rest of the desktop. Does anyone know how to make it fit all on to my screen. Thanks in advance.

         Brandon

---

### Post by wPwLUi3N on 2008-04-05
It may be a problem or a bug with your driver. 

If you use any other O.S. does same problem exist on that resolution?

---

### Post by skymera on 2008-04-05
Try to reconfigure Xorg and pick the resolutions you want.

```
 sudo dpkg-reconfigure -phigh xserver-xorg 
```

or alternatviely:
System > Prefs > Screen Resolution

---

### Post by bsiebert on 2008-04-05
I dual-boot with XP and in XP it works perfect. 

Yea, I've been messing with System>Preferences>Screen Resolution and System>Administration>Screens and Graphics but still cant seem to get anything to work.

Although that coding you set I understood but I typed it in then selected AMD then got a warning and nothing past that.

Thanks for your help do far!!

---

### Post by skymera on 2008-04-05
What warning? (screenshot =) )

When i have a res larger than my screen (mostly on my laptop) i reconfigure Xorg and select the max res the screen can have 1024x768 and its fine after that.

---

### Post by The Titan on 2008-04-05
> **skymera said:**
> What warning? (screenshot =) )

When i have a res larger than my screen (mostly on my laptop) i reconfigure Xorg and select the max res the screen can have 1024x768 and its fine after that.
this happened to me and it was because the resolution in my ubuntu options was different than the resolution in the nvidia-settings... I just changed them so they matched and voila!

---

### Post by bsiebert on 2008-04-05
it says:

xserver-xorg postinst warning: overwriting possibly-customised configuration file; backup in /etc/x11/xorg.conf.20080405190416
and then after that it sets me back to the regular cmd line.

once again Thanks!!

---

### Post by bsiebert on 2008-04-05
Ok so I got into Xorg and picked 1680x1050, 1440x900, and 1280x800 but still the resolution is still too big for the screen.

Thanks for the help!!

---

### Post by energy. on 2008-04-05
post your xorg.conf

---

### Post by bsiebert on 2008-04-05
Well I'm on my laptop because the computer that I'm working on won't stay connected to the net because Ubuntu and RALink wireless have issues so I'll type it out best I can, just the graphics and video parts.

Section "Device"
Identifier - "ATI RADEON 1650"
Driver - "ati"
BusID - "PCI:1:0:0"
EndSection

Section "Monitor"
Identifier - "LCM-22w3"
Option - "DPMS"
HorizSync -   30-82
VertRefresh -   56-76
EndSection

Section "Screen"
Identifier - "Default Screen"
Device -"ATI RADEON 1650"
Monitor - "LCM-22w3"
DefaulDepth - 24
Subsection "Display"
Modes - "1680x1050" "1440x900" "1280x800"
End Subsection
End Section

Section "ServerLayout"
Identifier - "Default Layout"
Screen - "Default Screen"
InputDevice - "Generic Keyboard"
InputDevice - "Configured Mouse"

Thats the graphics and video section. I have a feeling that it has to do something with the horizontal sync rates and the vertical refresh rates, but Im not sure about what they should be if they were wrong.

Thanks!!

---

### Post by energy. on 2008-04-05
Under section "Screen", Subsection "Display" add the line

```
Virtual 1680     1050
```

---

### Post by bsiebert on 2008-04-05
Woot working!! Now just to get my wireless to work. As soon as I boot up Firefox my wireless disconnects and I have to restart. Weird. If connect by using the Update Manager it never disconnects. 

Awesome thank you with the help on the resolution problem though!!

---

