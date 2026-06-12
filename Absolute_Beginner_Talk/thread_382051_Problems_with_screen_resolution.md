---
title: "Problems with screen resolution"
date: 2007-03-11
forum: Absolute Beginner Talk
---

### Post by Native Dialect on 2007-03-11
I am using a Sony LCD flat panel monitor (SMD M51). I can not get my resolution to go above 640x480 nor can I up my screen refresh rate beyond 60HZ. I am not sure how to resolve the problem, because the help file only indicates what features may be changed...rather than how to deal with them whey they can't be changed. Also, I set my Synaptic package to Universe, and I still can't find VLC Media Player (i'm using Edgy Eft). Has it been taken down, or am i just doing something wrong?

---

### Post by sad_iq on 2007-03-11
Your refresh rate could be fixed with the right video driver (Ati, Nvidia, Intel)...find instructions here: [http://ubuntuguide.org/wiki/Ubuntu_Edgy](http://ubuntuguide.org/wiki/Ubuntu_Edgy) .
 Also read about enabling the multiverse repository on the same link!!!

---

### Post by oilchangeguy on 2007-03-11
the refresh rate on an lcd is different from a crt. 60hz is fine on an lcd, and you'd go blind with a crt.

---

### Post by Native Dialect on 2007-03-11
Thanks, you guys are a life saver. I'll master this Linux business yet, and be rid of the woe of Windows XP :P

---

### Post by Pikestaff on 2007-03-11
If you are still having trouble with the resolution, try reconfiguring xorg:

```
sudo dpkg-reconfigure xserver-xorg
```

Choose mostly defaults for all the options, but be sure you select the right drivers when it asks, and when it gets to a part where it asks what resolutions you want to be able to display, choose the ones you want with the spacebar.  Then after you reboot you should be able to choose a higher resolution.  Good luck!!

---

### Post by kboykowboy on 2007-03-12
Hey All. This is my first post from my over cool Xubuntu install!!! YES!!! 

I have a variation of the above problem. My xorg.conf file looks as follows:

Section "Files"
        FontPath        "/usr/share/X11/fonts/misc"
        FontPath        "/usr/share/X11/fonts/cyrillic"
        FontPath        "/usr/share/X11/fonts/100dpi/:unscaled"
        FontPath        "/usr/share/X11/fonts/75dpi/:unscaled"
        FontPath        "/usr/share/X11/fonts/Type1"
        FontPath        "/usr/share/X11/fonts/100dpi"
        FontPath        "/usr/share/X11/fonts/75dpi"
        FontPath        "/usr/share/fonts/X11/misc"
        # path to defoma fonts
        FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
        Load    "i2c"
        Load    "bitmap"
        Load    "ddc"
        Load    "dri"
        Load    "extmod"
        Load    "freetype"
        Load    "glx"
        Load    "int10"
        Load    "type1"
        Load    "vbe"
EndSection

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "dk"
        Option          "XkbOptions"    "lv3:ralt_switch"
EndSection

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ExplorerPS/2"
        Option          "ZAxisMapping"          "4 5"
        Option          "Emulate3Buttons"       "true"
EndSection

Section "InputDevice"
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        Option          "SendCoreEvents"        "true"
        Option          "Device"                "/dev/psaux"
        Option          "Protocol"              "auto-dev"
        Option          "HorizScrollDelta"      "0"
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "stylus"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "stylus"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "eraser"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "eraser"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "cursor"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "cursor"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "Device"
        Identifier      "S3 Inc. 86C270-294 Savage/IX-MV"
        Driver          "savage"
        BusID           "PCI:1:1:0"
EndSection

Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
        HorizSync       28-51
        VertRefresh     43-60
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "S3 Inc. 86C270-294 Savage/IX-MV"
        Monitor         "Generic Monitor"
        DefaultDepth    16
        SubSection "Display"
                Depth           1
                Modes           "1024x768"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1024x768"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1024x768"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1024x768"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1024x768"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1024x768"
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
        InputDevice     "stylus" "SendCoreEvents"
        InputDevice     "cursor" "SendCoreEvents"
        InputDevice     "eraser" "SendCoreEvents"
        InputDevice     "Synaptics Touchpad"
EndSection

Section "DRI"
        Mode    0666
EndSection

However i'm not able to shift into 1024x768

can anyone help me out on this issue?!

---

### Post by kboykowboy on 2007-03-14
Really no one who can help?!

by the way my computer is a omnibook xe3l ([http://www.ciao.co.uk/HP_OmniBook_XE3L__5373335#productdetail](http://www.ciao.co.uk/HP_OmniBook_XE3L__5373335#productdetail))

I'm not really a computer wize, and i tryed to look at the possible resolution solutions, but i have a hard time determinding what problem i may have! 

Could it maybe be this one "Intel Graphics driver (i810) won't use high screen resolutions" on this page ([https://help.ubuntu.com/community/FixVideoResolutionHowto](https://help.ubuntu.com/community/FixVideoResolutionHowto))

Some one told me on the chat that i should change the refresh rates, but i have no clue about what they should be changed to and how?!

---

