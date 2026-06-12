---
title: "G5 TV out issues"
date: 2007-04-28
forum: Apple PPC Users
---

### Post by Kepesk on 2007-04-28
Hello!
I've installed Xubutu on my Powermac G5 with the intention of eventually making the video card output to my TV.  I've gotten to that point now, and while my video card (ATI Raedon 9600) doesn't have native video out, I've bought the Apple DVI to S-video adapter to output on my TV.  Unfortunately, it's not working.

I've tried it in OS X, and it worked, so I know it's possible.  I'velearned about editing my xorg.conf file, but I haven't found a modeline that works (and I've tried dozens)

Part of the problem seems to be that the Xubuntu monitor settings only seem to conform partially to my xorg.conf settings.  When I have a lot of stuff enabled in my xorg.conf, I see an increase in the Xubuntu monitor settings, but when I only have one or two enabled in xorg,  still see lots in Xubuntu settings.  And as a bonus, I only ever see one in a single resolution and refresh setting (I can't test two 640x480@60 modlines at once, for example).

I'm trying to output to an analog NTSC tv.  Specifically SANYO DS27930.  The manual says it should have 480i support, but I'm having trouble finding a 480i modeline that works.

I don't suppose anyone has any clue of whqat I might want to try next?

Thanks in advance!

-Jacob

---

### Post by stmiller on 2007-04-28
This is S-video out? I'm not sure if the current ppc radeon driver supports s-vid out.

---

### Post by Kepesk on 2007-04-28
Well, that would certainly be my issue!  How about composite?  The smae adapter has composite out..  Could that be made to work?

---

### Post by stmiller on 2007-04-29
Okay yes I see now. That should work. You'll have to make a fairly custom xorg.conf file for this. One like this: (only relevant portions shown here)


```
Section "ServerFlags"	 
    Option "Xinerama" "On"	 
EndSection	 

Section "Module"	 
    Load "dbe" # Double-Buffering Extension	 
    Load "v4l" # Video for Linux	 
    Load "extmod"	 
    Load "type1"	 
    Load "freetype"	 
    Load "glx"	 
    Load "dri"	 
EndSection	 
	 
...	 
Section "Device"	 
    Identifier "device0"	 
    VendorName "ATI"	 
    BoardName "ATI Radeon"	 
    Driver "radeon"	 
    BusID "PCI:1:0:0"	 
    Screen 0	 
EndSection	 
	 
Section "Device"	 
    Identifier "device1"	 
    BoardName "ATI Radeon"	 
    Driver "radeon"	 
    BusID "PCI:1:0:0"
    Screen 1
EndSection

Section "Monitor"
    Identifier "monitor0"
    Option "DPMS"
EndSection

Section "Monitor"
    Identifier "monitor1"
    Option "DPMS"
EndSection

Section "Screen"
    Identifier "Screen0"
    Device "device0"
    Monitor "monitor0"
    DefaultColorDepth 24
    Subsection "Display"
        Depth 24
        Virtual 1280 1024
        Modes    "1280x1024"
    EndSubsection
EndSection

Section "Screen"
    Identifier "Screen1"
    Device "device1"
    Monitor "monitor1"
    DefaultColorDepth 24
    Subsection "Display"
        Depth 24
        Virtual 1280 1024
        Modes    "1280x1024"
    EndSubsection
EndSection

Section "ServerLayout"
    Identifier "Multihead layout"
    InputDevice "Keyboard1" "CoreKeyboard"
    InputDevice "Mouse0" "CorePointer"
    Screen  "Screen0" 0 0
    Screen  "Screen1" RightOf "Screen0"
EndSection
```

---

