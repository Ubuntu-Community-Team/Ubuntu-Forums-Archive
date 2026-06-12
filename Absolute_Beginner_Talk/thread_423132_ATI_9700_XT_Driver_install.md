---
title: "ATI 9700 XT Driver install"
date: 2007-04-25
forum: Absolute Beginner Talk
---

### Post by Bogomip on 2007-04-25
SO I somewhat foolishly re-ventured into the world of linux again yesterday and have been trying to install graphics drivers ever since, specifically ATI drivers.

I have been following this guide...

[http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide#Ubuntu-specific_Issues](http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide#Ubuntu-specific_Issues)

to no avail, whenever I type fglrxinfo all I get is stuff about a mesa driver, not my ati driver at all. 

Im installing in a terminal window, though someone in a thread here ([http://forums.bit-tech.net/showthread.php?p=1464853#post1464853](http://forums.bit-tech.net/showthread.php?p=1464853#post1464853)) said something about runlevel 3, which also did nothing apart from when i type runlevel it now says 3 - I dont know what it said before...

I don't really know what else to tell you about my problem as I get no error messages and have taken every route through that guide to the keystroke :S

EDIT: Oh, so sorry - im running 7.04 Feisty! :)

---

### Post by Talon2 on 2007-04-25
> **Bogomip said:**
> SO I somewhat foolishly re-ventured into the world of linux again yesterday and have been trying to install graphics drivers ever since, specifically ATI drivers.

I have been following this guide...

[http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide#Ubuntu-specific_Issues](http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide#Ubuntu-specific_Issues)

to no avail, whenever I type fglrxinfo all I get is stuff about a mesa driver, not my ati driver at all. 

Im installing in a terminal window, though someone in a thread here ([http://forums.bit-tech.net/showthread.php?p=1464853#post1464853](http://forums.bit-tech.net/showthread.php?p=1464853#post1464853)) said something about runlevel 3, which also did nothing apart from when i type runlevel it now says 3 - I dont know what it said before...

I don't really know what else to tell you about my problem as I get no error messages and have taken every route through that guide to the keystroke :S

EDIT: Oh, so sorry - im running 7.04 Feisty! :)

Is 7.04 not detecting and installing the Radeon open source driver?

The reason I ask is that I have a box with a ATI 9600 which works very well to include Desktop Effects and I didn't even have to tweek xorg.conf.

---

### Post by Bogomip on 2007-04-25
How did you do it ? What do you get when you type fglrxinfo ?

---

### Post by freebird54 on 2007-04-25
fglrxinfo is associated ony with the fglrx driver - the proprietary one from ATI.  This is not used by default in Feisty -and probably isn't needed.  I ran fglrx on Edgy, but haven't bothered on Feisty (yet, anyway) because I didn't need XGL to get beryl et al working.

If you want fglrx to work, I have a couple of fixes that worked on Edgy you can have - or you can just dump the fglrx method and enjoy decent performance on the 'ati' or 'radeon' drivers....

---

### Post by Bogomip on 2007-04-25
what do you use?! Im horribly confused! So fglrx IS ati ? the guide said I had to rename the ati driver to fglrx in the xorg.conf!

Im trying to get games running under wine and the direct3d is awful and the opengl isnt yet working - if that helps with my problem!

---

### Post by freebird54 on 2007-04-25
There are 2 kinds of drivers for ATI cards.  One kind is the one that started you off when you installed.  These are open source drivers, provided by the community, and handled by an xprg.conf entry of 'ati'.

ATI themselves have provided a partial functionality driver for Linuz that is NOT open source, called gflrx. *IF* the 'ati' driver doesn't work, you can go to the fglrx drivers.  This is what I did in Edgy, because I wasn't getting the resolutions I wanted, and I couldn't run Beryl.

In Feisty, the ati driver seems to be improved at least to the level where it runs a 9550 radeon quite well.  I undestand that the newer 'X###' cards are NOT well supported that way - they need the fglrx drivers.

I don't play a lot of games anymore (at least not on Intel-based hardware) so I don't know which works better for things under wine - or even if there is a difference.  

Should I post what ATI based xorg.conf files look like for the 2 alternatives?  I have both :)

---

### Post by Bogomip on 2007-04-25
Yes, that would be great thanks!

Theres a thing on that website I linked that tells me how to revert to my origonal drivers - im gonna try that now, even if i cant get the resolution I want at least I can play some games to releif all this revision/exam/+linux stress!

---

### Post by freebird54 on 2007-04-25
OK - here is a fglrx-based xorg.conf file.  I'll **bold** anything I think important to proper functionality.  The other will be a couple of minutes - I have to mount my Feisty drives :)

```
# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the /etc/X11/xorg.conf manual page.
# (Type "man /etc/X11/xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "ServerLayout"
        Identifier     "Default Layout"
        Screen         "Default Screen" 0 0
        InputDevice    "Generic Keyboard"
        InputDevice    "Configured Mouse"
        InputDevice    "stylus" "SendCoreEvents"
        InputDevice    "cursor" "SendCoreEvents"
        InputDevice    "eraser" "SendCoreEvents"
EndSection

Section "Files"

        # path to defoma fonts
        FontPath     "/usr/share/X11/fonts/misc"
        FontPath     "/usr/share/X11/fonts/cyrillic"
        FontPath     "/usr/share/X11/fonts/100dpi/:unscaled"
        FontPath     "/usr/share/X11/fonts/75dpi/:unscaled"
        FontPath     "/usr/share/X11/fonts/Type1"
        FontPath     "/usr/share/X11/fonts/100dpi"
        FontPath     "/usr/share/X11/fonts/75dpi"
        FontPath     "/usr/share/fonts/X11/misc"
        FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
        Load  "bitmap"
        Load  "ddc"
        Load  "dri"
        Load  "extmod"
        Load  "freetype"
        Load  "glx"
        Load  "int10"
        Load  "type1"
        Load  "vbe"
EndSection

[B]Section "ServerFlags"
        Option      "AIGLX" "off"
EndSection
[/B]
Section "InputDevice"
        Identifier  "Generic Keyboard"
        Driver      "kbd"
        Option      "CoreKeyboard"
        Option      "XkbRules" "xorg"
        Option      "XkbModel" "pc104"
        Option      "XkbLayout" "us"
        Option      "XkbOptions" "lv3:ralt_switch"
EndSection

Section "InputDevice"
        Identifier  "Configured Mouse"
        Driver      "mouse"
        Option      "CorePointer"
        Option      "Device" "/dev/input/mice"
        Option      "Protocol" "ExplorerPS/2"
        Option      "ZAxisMapping" "4 5"
        Option      "Emulate3Buttons" "true"
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
        Identifier  "stylus"
        Driver      "wacom"
        Option      "Device" "/dev/wacom"          # Change to 
        Option      "Type" "stylus"
        Option      "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
        Identifier  "eraser"
        Driver      "wacom"
        Option      "Device" "/dev/wacom"          # Change to 
        Option      "Type" "eraser"
        Option      "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
        Identifier  "cursor"
        Driver      "wacom"
        Option      "Device" "/dev/wacom"          # Change to 
        Option      "Type" "cursor"
        Option      "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "Monitor"
        Identifier   "Samsung_900iFT"
[B]        HorizSync    30.0 - 100.0
        VertRefresh  50.0 - 160.0[/B]
        Option      "DPMS"
EndSection

Section "Device"
        Identifier  "ATI Radeon 9550"
        Driver      "fglrx"
[B]        Option      "UseFBDev" "true"
        Option      "VideoOverlay" "on"
        Option      "OpenGLOverlay" "off"[/B]
        BusID       "PCI:1:0:0"
EndSection

Section "Screen"
        Identifier "Default Screen"
        Device     "ATI Radeon 9550"
        Monitor    "Samsung_900iFT"
        DefaultDepth     24
        SubSection "Display"
                Depth     1
                Modes    "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth     4
                Modes    "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth     8
                Modes    "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth     15
                Modes    "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth     16
                Modes    "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth     24
                Modes    "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
        EndSubSection
EndSection

Section "DRI"
        Mode         0666
EndSection

[B]Section "Extensions"
        Option      "Composite" "Disable"
EndSection[/B]
```

The CORRECT numbers for HrizSync and VertRefresh are the key to proper resolutions, regardless of driver.  AIGLX off is key to running XGL for Beryl et al.  Composite disabled is necessary for fglrx drivers - as are 2 of the 2 Options in the device entry for fglrx...  The other is coming in a minute or 2...

---

### Post by freebird54 on 2007-04-25
Here is Feisty xorg.conf - with 'ati' drivers and settings...

```
# /etc/X11/xorg.conf (xorg X Window System server configuration file)
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
        Load    "dbe"
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
        Option          "XkbModel"      "pc101"
        Option          "XkbLayout"     "us"
        Option          "XkbOptions"    "lv3:ralt_switch"
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
        Option          "Device"        "/dev/wacom"    # Change to 
                                                        # /dev/input/event
                                                        # for USB
        Option          "Type"          "stylus"
        Option          "ForceDevice"   "ISDV4"         # Tablet PC ONLY
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "eraser"
        Option          "Device"        "/dev/wacom"    # Change to 
                                                        # /dev/input/event
                                                        # for USB
        Option          "Type"          "eraser"
        Option          "ForceDevice"   "ISDV4"         # Tablet PC ONLY
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "cursor"
        Option          "Device"        "/dev/wacom"    # Change to 
                                                        # /dev/input/event
                                                        # for USB
        Option          "Type"          "cursor"
        Option          "ForceDevice"   "ISDV4"         # Tablet PC ONLY
EndSection

Section "Device"
        Identifier      "ATI Technologies Inc RV350 AS [Radeon 9550]"
        Driver          "ati"
[B]        Option          "EnablePageFlip" "true"
        Option          "RenderAccel" "true"
        Option          "ColorTiling" "on"
        Option          "AccelMethod" "XAA"
        Option          "XAANoOffscreenPixmaps" "on"
        #Option         "AGPFastWrite" "on"
        #Option         "AGPMode" "4"
        Option          "AGPSize" "32"[/B]
        BusID           "PCI:1:0:0"
EndSection

Section "Monitor"
        Identifier      "Samsung 900IFT"
        Option          "DPMS"
[B]        HorizSync       28-100
        VertRefresh     50-160[/B]
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "ATI Technologies Inc RV350 AS [Radeon 9550]"
        Monitor         "Samsung 900IFT"
        DefaultDepth    24
        SubSection "Display"
                Depth           1
                Modes           "1280x1024" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1280x1024" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1280x1024" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1280x1024" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1280x1024" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1280x1024" "1024x768" "800x600" "640x480"
        EndSubSection
EndSection

Section "ServerLayout"
**        Option          "AIGLX" "true"**
        Identifier      "Default Layout"
        Screen          "Default Screen"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
        InputDevice     "stylus"        "SendCoreEvents"
        InputDevice     "cursor"        "SendCoreEvents"
        InputDevice     "eraser"        "SendCoreEvents"
EndSection

Section "DRI"
        Mode    0666
EndSection

[B]Section "Extensions"
        Option "Composite" "Enable"
EndSection[/B]
```

You will notice some differences!  AIGLX is TRUE for this one, Composite is ENABLED for this one, and different options are mentioned in the device 'ati' section.  Still important to have your monitor correctly identified.

More to come if needed (ie: the mesa cure if using fglrx) - but you shouldn't need it if wine performance is OK with ati.

---

### Post by Bogomip on 2007-04-25
thanks alot, I am working on it atm - my main concern is that ive tried installing and reinstalling os much its all very confused now :( Must have installed it at least 10 times by now, very frustrating :<

---

### Post by freebird54 on 2007-04-25
The biggest problem is trying to do it all at once. Bit me a few times at the beginning too.  One tends to assume that one possesses more knowledge than is the fact!  This machine and OS don't care that I've done this since '82... :)

---

