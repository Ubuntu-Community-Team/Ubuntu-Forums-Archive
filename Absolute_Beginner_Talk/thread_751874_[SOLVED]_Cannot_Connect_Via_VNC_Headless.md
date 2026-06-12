---
title: "[SOLVED] Cannot Connect Via VNC Headless"
date: 2008-04-11
forum: Absolute Beginner Talk
---

### Post by effinboy on 2008-04-11
So I've been getting used to using linux after converting an old PC into a home media server. Everythings been going great now for about a year, I now want to remove the monitor, and place the server in the closet.

I use tightvnc on vista and xp, and cannot get in...
My ports are still forwarded and I can still get in via putty.

After reading some terminal output, it sounds like X is not starting when I do not have a monitor hooked up, and that without X, my vnc server will not work. I've tried different VNC servers and attempted to start them manually in case X was what was starting them in the first place.

What do I need to do to get this working? 
Can X be reset (in case its the settings in it's conf), can I force it to start without a monitor? 
Is there a VNC server that is NOT dependant upon X?

Thanks for your help!

---

### Post by Mithrilhall on 2008-04-11
This is what I did to use vnc with no monitor/keyboard/mouse.

```

sudo apt-get install vnc4server

```

Make sure vnc4server is running...

```

/usr/bin/openvt -fwc 2 -- /bin/su - USERNAME -c /usr/bin/startx >& /dev/null

```

Once I connect via vnc I start the kicker...
```

kicker

```

Keep in mind I have KDE running as my DE.

---

### Post by effinboy on 2008-04-11
Thanks Mithrilhall, But I got GDE going already, and everything else is all good to go except this. 

I'm pretty sure the issue lies within my xorg.conf 

Anyone know what it might be?



Here's my current xorg.conf

```
Section "Files"
EndSection

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "us"
EndSection

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ImPS/2"
        Option          "ZAxisMapping"          "4 5"
        Option          "Emulate3Buttons"       "true"
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "stylus"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"          "stylus"
        Option          "ForceDevice"   "ISDV4"         # Tablet PC ONLY
EndSection


Section "Device"
        Identifier      "ATI Technologies Inc Radeon RV100 QY [Radeon 7000/VE]"
        Driver          "ati"
        BusID           "PCI:0:9:0"
EndSection

Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
        HorizSync       31-101
        VertRefresh     60-160
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "ATI Technologies Inc Radeon RV100 QY [Radeon 7000/VE]"
        Monitor         "Generic Monitor"
        DefaultDepth    24
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"

# Uncomment if you have a wacom tablet
#       InputDevice     "stylus"        "SendCoreEvents"
#       InputDevice     "cursor"        "SendCoreEvents"
#       InputDevice     "eraser"        "SendCoreEvents"
EndSection

```

---

### Post by effinboy on 2008-04-11
Does anyone have an answer for this? I know I should be a bit more patient, but I need to get rid of this monitor before I move tomorrow (technically today at this hour)

---

### Post by Mithrilhall on 2008-04-11
You could always try what I have recommended above. Just change out the "startx" to the command you Gnome people use. :)

---

### Post by effinboy on 2008-04-11
Got it to work.

It seem that X wouldn't start because of the proprietary video card driver for the Radeon card I had installed. So I dropped in an older generic video card, started up in recovery mode via grub, did dpkg-reconfigure xserver-xorg, rebooted, and everything worked just fine.

If anyone seems to have issues with this kind of a problem, try another video card!

Thanks for your attempts to help Mithrilhall!

---

