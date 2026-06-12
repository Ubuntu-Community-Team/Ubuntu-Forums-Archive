---
title: "Screen Resolution"
date: 2007-11-05
forum: Absolute Beginner Talk
---

### Post by Neil Purling on 2007-11-05
I have had a installation of Ubuntu 6.06 "Dapper Drake"  running with no problems.
This evening Ubuntu started with 640x480 screen resolution and I cannot find the higher resolution of 800X600 I regard as normal.
How do I get it back to normal operation?

---

### Post by mikewhatever on 2007-11-05
Can you post your xorg.conf file,
> cat /etc/X11/xorg.conf

---

### Post by Neil Purling on 2007-11-05
As requested :

Section "Monitor"
        Identifier      "TE555"
        Option          "DPMS"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "NVIDIA Corporation NV34 [GeForce FX 5200]"
        Monitor         "TE555"
        DefaultDepth    24
        SubSection "Display"
                Depth           1
                Modes           "1024x768" "800x600"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1024x768" "800x600"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1024x768" "800x600"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1024x768" "800x600"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1024x768" "800x600"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1024x768" "800x600"
        EndSubSection

---

### Post by Neil Purling on 2007-11-05
I restored the default xorg.conf to :
Section "Screen"
        Identifier      "Default Screen"
        Device          "NVIDIA Corporation NV34 [GeForce FX 5200]"
        Monitor         "TE555"
        DefaultDepth    24
        SubSection "Display"
                Depth           1
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1024x768" "800x600" "640x480"

Either way the Screen Resolution Preferences box only had the default  options of 640x480 at 60hz refresh rate. I would want a default setting of 800x600 resolution, and no lower than that.

---

### Post by magiceraser06 on 2007-11-05
Hey Neil.

You don't really need all those mode lilnes.  You should be fine with the following:


```
Depth 24
Modes "1280x1024"  "1024x768" "800x600" "640x480"
```


Then you'll want to do a full restart.  If that doesn't work, you might want to make sure your RESCTRICTED drivers are enabled and being used.

For my xorg.conf, I only have  Depth 24  and Modes "1280x1024",   even with that setting, all lower resolutions are detected.

let me know.



ONE MORE THING:
Oh yeah, you may also need to manually adjust your monitors horizontal and vertical refresh values.  You would have to look it up to find out the correct values.  I had this issue on my Dell Latitude C600.

---

### Post by Neil Purling on 2007-11-05
I do a full restart.
I know nothing has changed when the logon box is too large.
As I log on the toolbar initially appears with the smaller apparent size of the text which jumps to the larger size??
System --- Preferences --- Screen Resolution still only has choice of 640x480 @ 60hz refresh rate.
How do I need to make sure those restricted drivers are being used?

---

### Post by magiceraser06 on 2007-11-05
What version of Ubuntu are you using?  Gutsy should let you know your using the restricted drivers by displaying an icon in the toolbar, top right.  it will look like a PCI card or Vido Card symbol.  

you can also check if your restricted drivers are needed/used by going to SYSTEM --> ADMINISTRATION --> RESTRICTED DRIVER MANAGER

keep us posted.

---

### Post by Neil Purling on 2007-11-21
I  Have version 6.06. This is important because it is like it isn't loading the proper drivers as the system boots. After multiple restarts all I get is 640x480, with no alternatives on offer.
I need to make the minimum default 800x600.
The last time it did this I got so annoyed I did a full re-install. Now it's doing it again............. Why?
Is there anything I can do using the official Canonical Ubuntu disc?

---

### Post by Neil Purling on 2007-11-21
I shut down and let it sulk for a while.
Upon re-starting all was well.
Why does it throw a fit like this occaisionally?

---

### Post by Dr. Cox on 2007-11-21
hi there, 

i'm using an acer tm290 laptop with a display that supports 1400x1050 resolution.  however, i cannot get gnome to use the settings.

what can i do?

here's my xorg.conf

>   # /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf(5) manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
        FontPath        "/usr/share/fonts/X11/misc"
        FontPath        "/usr/share/fonts/X11/cyrillic"
        FontPath        "/usr/share/fonts/X11/100dpi/:unscaled"
        FontPath        "/usr/share/fonts/X11/75dpi/:unscaled"
        FontPath        "/usr/share/fonts/X11/Type1"
        FontPath        "/usr/share/fonts/X11/100dpi"
        FontPath        "/usr/share/fonts/X11/75dpi"
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
        Load    "vbe"
EndSection

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "de"
        Option          "XkbVariant"    "nodeadkeys"
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
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        Option          "SendCoreEvents"        "true"
        Option          "Device"                "/dev/psaux"
        Option          "Protocol"              "auto-dev"
        Option          "HorizScrollDelta"      "0"
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "stylus"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"          "stylus"
        Option          "ForceDevice"   "ISDV4"         # Tablet PC ONLY
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "eraser"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"          "eraser"
        Option          "ForceDevice"   "ISDV4"         # Tablet PC ONLY
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "cursor"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"          "cursor"
        Option          "ForceDevice"   "ISDV4"         # Tablet PC ONLY
EndSection

Section "Device"
        Identifier      "Intel Corporation 82852/855GM Integrated Graphics Device"
        Driver          "i810"
        BusID           "PCI:0:2:0"
EndSection

Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
        HorizSync       28-70
        VertRefresh     43-60
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "Intel Corporation 82852/855GM Integrated Graphics Device"
        Monitor         "Generic Monitor"
        DefaultDepth    24
        SubSection "Display"
                Depth           1
                Modes           "1400x1050"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1400x1050"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1400x1050"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1400x1050"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1400x1050"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1400x1050"
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
        InputDevice     "stylus"        "SendCoreEvents"
        InputDevice     "cursor"        "SendCoreEvents"
        InputDevice     "eraser"        "SendCoreEvents"
        InputDevice     "Synaptics Touchpad"
EndSection

Section "DRI"
        Mode    0666
EndSection
  

---

### Post by Aquilastudio.com on 2007-11-21
reconfigure xserver

---

