---
title: "[SOLVED] Screen Resolution/Video Driver issue"
date: 2008-04-07
forum: Arch and derivatives
---

### Post by arbulus on 2008-04-07
I posted a question over in the Arch forums and haven't got an answer yet, so I thought I'd try my question here as well.

I've googled myself stupid with this.  I've search through the arch wiki and followed all the instructions but I'm still having trouble.

I'm pretty new to Arch, so please bear with me.
I just installed arch on an old Dell Dimension 2400 with Intel 82845 graphics card.  i installed the i810 video driver because the "intel" driver didn't work at all for me. I have a 22" monitor with a native resolution of 1680x1050.  But I can't seem to get that resolution.  It keeps giving me 1600x1200 which is very odd.  When I move the mouse around the screen, the monitor pans across moving the desktop around. 

I've used hwd to try to configure xorg, but it doesn't detect my usb mouse and keyboard and doesn't work at all.  When I start x it says no screens found.  I've tried x -configure and that gives me a working xorg but with this incorrect resolution.  I've edited the xorg.conf file by hand to try to make it work but just ignores my changes.  I tried changing the resolution to 1440x900 to see if that would work, but it still won't see it.  It's like it's completely stuck at 1600x1200.

I'm running just openbox for a gui. 

Here is my xorg.conf file:
```

Section "ServerLayout"
    Identifier     "X.org Configured"
    Screen      0  "Screen0" 0 0
    InputDevice    "Mouse0" "CorePointer"
    InputDevice    "Keyboard0" "CoreKeyboard"
EndSection

Section "Files"
    RgbPath      "/usr/share/X11/rgb"
    ModulePath   "/usr/lib/xorg/modules"
    FontPath     "/usr/share/fonts/misc"
    FontPath     "/usr/share/fonts/100dpi:unscaled"
    FontPath     "/usr/share/fonts/75dpi:unscaled"
    FontPath     "/usr/share/fonts/TTF"
    FontPath     "/usr/share/fonts/Type1"
EndSection

Section "Module"
    Load  "extmod"
    Load  "glx"
    Load  "dri"
    Load  "record"
    Load  "GLcore"
    Load  "dbe"
    Load  "xtrap"
    Load  "freetype"
EndSection

Section "InputDevice"
    Identifier  "Keyboard0"
    Driver      "kbd"
EndSection

Section "InputDevice"
    Identifier  "Mouse0"
    Driver      "mouse"
    Option        "Protocol" "auto"
    Option        "Device" "/dev/input/mice"
    Option        "ZAxisMapping" "4 5 6 7"
EndSection

Section "Monitor"
    #DisplaySize      470   300    # mm
    Identifier   "Monitor0"
    VendorName   "WDE"
    ModelName    "LCM-22w3"
 ### Comment all HorizSync and VertRefresh values to use DDC:
    HorizSync    30.0 - 82.0
    VertRefresh  56.0 - 76.0
    Option        "DPMS"
EndSection

Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz"
        ### [arg]: arg optional
        #Option     "NoAccel"                # [<bool>]
        #Option     "SWcursor"               # [<bool>]
        #Option     "ColorKey"               # <i>
        #Option     "CacheLines"             # <i>
        #Option     "Dac6Bit"                # [<bool>]
        #Option     "DRI"                    # [<bool>]
        #Option     "NoDDC"                  # [<bool>]
        #Option     "ShowCache"              # [<bool>]
        #Option     "XvMCSurfaces"           # <i>
        #Option     "PageFlip"               # [<bool>]
    Identifier  "Card0"
    Driver      "i810"
    VendorName  "Intel Corporation"
    BoardName   "82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device"
    BusID       "PCI:0:2:0"
EndSection

Section "Screen"
    Identifier "Screen0"
    Device     "Card0"
    Monitor    "Monitor0"
    DefaultDepth    24
    SubSection "Display"
        Viewport   0 0
        Depth     24
        Modes    "1440x900"
    EndSubSection
EndSection
```

Anyone have any ideas what I can do to resolve this?

---

### Post by OffAxis on 2008-04-07
Have you tried reconfiguring the x-server from the command line?

1. Look up your monitor's specs online (refresh rates, available resolutions, etc).
2. backup your xorg.conf file
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
```

3. run the reconfigure utility
```
sudo dpkg-reconfigure xserver-xorg
```

This'll let you specify every aspect of your xserver setup, including video driver, monitor resolution, etc.

4. restart the x-server.
[B]CTRL+ALT+Backspace
[/B]

---

### Post by arbulus on 2008-04-07
> **OffAxis said:**
> Have you tried reconfiguring the x-server from the command line?

1. Look up your monitor's specs online (refresh rates, available resolutions, etc).
2. backup your xorg.conf file
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
```

3. run the reconfigure utility
```
sudo dpkg-reconfigure xserver-xorg
```

This'll let you specify every aspect of your xserver setup, including video driver, monitor resolution, etc.

4. restart the x-server.
[B]CTRL+ALT+Backspace
[/B]

I tried that one.  dpkg-reconfigure doesn't seem to work in Arch.

---

### Post by kpkeerthi on 2008-04-08
dpkg-reconfigure is debian's. Check [this]("http://ubuntuforums.org/showthread.php?t=716560") out for some useful and effective ways to configure X in arch.

As a side note I had some trouble configuring my USB laser mouse with Arch but had no trouble with Ubuntu. I quickly copied xorg.conf off Ubuntu live CD over Arch's. Problem solved.

---

### Post by arbulus on 2008-04-08
Ok, so I came across this command "xrandr" to refer to your screen resolution settings.  This is the output of that command for me:

```
Screen 0: minimum 640 x 480, current 1600 x 1200, maximum 1600 x 1200
default connected 1600x1200+0+0 (normal left inverted right) 0mm x 0mm
   1280x1024      75.0  
   1024x768       75.0  
   800x600        75.0  
   640x480        75.0  
   1600x1200      75.0*
```

Since 1680x1050 is not listed on this, does that mean that my card is not capable of 1680x1050?  I'm not terribly familiar with this.

---

### Post by arbulus on 2008-04-08
Well, I just answered my own question. I pulled a 17" CRT monitor out of the closet just to see if it could get the correct resolution.  I plugged in my monitor and had to do X -configure again, but it works like a charm now with the correct 1280x1024 resolution for this monitor.  so I guess my video card just couldn't handle the 1680x1024 resolution.

Thanks for your help, though!

---

### Post by fwojciec on 2008-04-08
You could try adding a modeline, something like this:
> ModeLine        "1680x1050" 146.2 1680 1784 1960 2240 1050 1053 1059 1089
To the "monitor" section in xorg.conf -- maybe it would help you get the desired resolution.

I'm not sure if this modeline would be appropriate for your monitor thought -- I never had to use one myself -- you can try generating a modeline using this: [http://xtiming.sourceforge.net/cgi-bin/xtiming.pl]("http://xtiming.sourceforge.net/cgi-bin/xtiming.pl")

And here is an interesting example of xorg.conf that's set up for the resolution you're trying to achieve -- it does it a little differently, maybe it'll be helpful as well: [http://paste.lisp.org/display/45255]("http://paste.lisp.org/display/45255")

---

### Post by arbulus on 2008-04-08
> **fwojciec said:**
> You could try adding a modeline, something like this:

To the "monitor" section in xorg.conf -- maybe it would help you get the desired resolution.

I'm not sure if this modeline would be appropriate for your monitor thought -- I never had to use one myself -- you can try generating a modeline using this: [http://xtiming.sourceforge.net/cgi-bin/xtiming.pl]("http://xtiming.sourceforge.net/cgi-bin/xtiming.pl")

And here is an interesting example of xorg.conf that's set up for the resolution you're trying to achieve -- it does it a little differently, maybe it'll be helpful as well: [http://paste.lisp.org/display/45255]("http://paste.lisp.org/display/45255")


Thank you!  That's some great info there.  I'll give those a try and see what happens.

---

