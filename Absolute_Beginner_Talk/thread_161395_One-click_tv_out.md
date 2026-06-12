---
title: "One-click tv out"
date: 2006-04-16
forum: Absolute Beginner Talk
---

### Post by trent dillman on 2006-04-16
How can I get videos to play on a tv that was not plugged in while booting? Is there a way to specify a video output that just plays videos on my TV?

---

### Post by gerbman on 2006-04-17
> How can I get videos to play on a tv that was not plugged in while booting?Does CTRL+ALT+BACKSPACE do the trick? (it'll restart your session, in case you have something open you care about).

> Is there a way to specify a video output that just plays videos on my TV?I don't quite understand. I have dual monitor output set up with my ATI 9500, the TV being hooked up to the s-video output, and starting a movie on the TV is as easy as running the command from the TV's desktop space.

---

### Post by trent dillman on 2006-04-17
Sorry to not be specific. I'm trying to get videos to play on a tv that isn't plugged in at boot, as this is on a laptop and the TV isn't always plugged. I don't want/care for a dual-head display as much as I just want videos to play on the TV.

Well, here's where I'm at:

I have my xorg.conf with separate layouts, etc., for tv and without:

```
Section "Device"
        Identifier      "NVIDIA Corporation NV36 [GeForce FX Go5700]"
        Driver          "nvidia"
        BusID           "PCI:1:0:0"
        Option          "NvAGP"         "1"
        Option          "NoLogo"        "true"
        Option          "SWCursor"      "1"
        Option          "HWCursor"      "0"
        Option          "ConnectedMonitor"      "DFP"
        Screen          0
EndSection

Section "Device"
        Identifier      "TV"
        Driver          "nvidia"
        BusID           "PCI:1:0:0"
        Option          "NvAGP"         "1"
        Option          "NoLogo"        "true"
        Option          "SWCursor"      "1"
        Option          "HWCursor"      "0"
        Option          "TVStandard"    "NTSC"
        Option          "TVOutFormat"   "SVIDEO"
        Option          "ConnectedMonitor"      "TV"
        Screen          1
EndSection

Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
        HorizSync       28-72
        VertRefresh     43-60
EndSection

Section "Monitor"
        Identifier      "tv"
        HorizSync       30-50
        VertRefresh     60
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "NVIDIA Corporation NV36 [GeForce FX Go5700]"
        Monitor         "Generic Monitor"
        DefaultDepth    16
        SubSection "Display"
                Depth           1
                Modes           "1440x900"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1440x900"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1440x900"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1440x900"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1440x900"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1440x900"
        EndSubSection
EndSection

Section "Screen"
        Identifier      "Screen_tv"
        Device          "TV"
        Monitor         "tv"
        DefaultDepth 16
        SubSection "Display"
                Depth   16
                Modes "1024x768" "800x600"
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          0 "Default Screen" 0 0
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
        InputDevice     "Synaptics Touchpad"
EndSection

Section "ServerLayout"
        Identifier     "tv"
        Screen         1  "Screen_tv"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
        InputDevice     "Synaptics Touchpad"
EndSection
```

Then, I made a script at /usr/local/bin/mplayer.tv:

```

#!/bin/bash
echo "$@" > /tmp/tvcommand
xauth add "$(/bin/hostname)/unix:1" MIT-MAGIC-COOKIE-1 $( xauth list | egrep "$(/bin/hostname)/unix:" | awk '{print $3}' )
/usr/bin/xinit /usr/bin/xterm -ut -e /usr/bin/mplayer -stop-xscreensaver -fs -vo sdl "$@" -- /usr/bin/X :1 -layout tv

```

Then I have an action set up in Nautilus called 'Play on TV...' that executes gksudo mplayer.tv %d/%f

TV Out works on-the-fly (the S-Video can be hotplugged), but I lose my X session until the video ends, or I quit mplayer. I know, I could CTRL+ALT+BKSP the X server or CTRL+ALT+F? back, but I'm really trying to get this to run with my X session. I'm looking now into using 'gdmdynamic', but so far have had no luck.

---

