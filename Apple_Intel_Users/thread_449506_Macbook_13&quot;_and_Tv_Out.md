---
title: "Macbook 13&quot; and Tv Out"
date: 2007-05-20
forum: Apple Intel Users
---

### Post by Ilove2023 on 2007-05-20
Hello!

I run feisty on my Macbook and I can't get the tv out to work. I have the s-video adapter from Apple (which works nice in OSX) but it seems impossible to have that in ubuntu (or Linux in general).

I give you my "best" xorg.conf. Actually it doesn't work but with this, I see something moving on the TV ;) ...

Note that I use " Option "MonitorLayout" "CRT,LFP"" because if I replace CRT by TV, my tv is totally black...

Does someone try the tv-out with the macbook ? ... please, help me ! ;)
```

Section "Device"
    Identifier    "Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller"
    Driver        "i810"
    BusID        "PCI:0:2:0"
    Screen 0
    Option "DDCMode" "True"
    Option "MonitorLayout" "CRT,LFP"
EndSection


Section "Device"
    Identifier    "deviceTV"
    Driver        "i810"
    BusID        "PCI:0:2:0"
    Screen 1
    Option "DDCMode" "True"
    Option "MonitorLayout" "CRT,LFP"
    Option "TVStandard"    "PAL-B"
    Option "TVOutFormat"    "SVIDEO"
EndSection

Section "Monitor"
    Identifier    "Generic Monitor"
    Option        "DPMS"
    HorizSync    28-64
    VertRefresh    43-60
EndSection

Section "Monitor"
    Identifier    "tv"
    Option        "DPMS"
        HorizSync        30-50
        VertRefresh        30-50
EndSection


Section "Screen"
    Identifier    "Default Screen"
    Device        "Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller"
    Monitor        "Generic Monitor"
    DefaultDepth    24
    SubSection "Display"
        Depth        1
        Modes        "1280x800"
    EndSubSection
    SubSection "Display"
        Depth        4
        Modes        "1280x800"
    EndSubSection
    SubSection "Display"
        Depth        8
        Modes        "1280x800"
    EndSubSection
    SubSection "Display"
        Depth        15
        Modes        "1280x800"
    EndSubSection
    SubSection "Display"
        Depth        16
        Modes        "1280x800"
    EndSubSection
    SubSection "Display"
        Depth        24
        Modes        "1280x800" "1024x768" "8OOx600"
    EndSubSection
EndSection

Section "Screen"
    Identifier    "screenTV"
    Device        "deviceTV"
    Monitor        "tv"
    DefaultDepth    24
    SubSection "Display"
        Depth        16
        Modes        "1024x768" "8OOx600"
    EndSubSection
    SubSection "Display"
        Depth        24
        Modes        "1024x768" "8OOx600"
    EndSubSection
EndSection

Section "ServerLayout"
    Identifier    "Default Layout"
    Screen 0    "Default Screen"
    Screen 1         "screenTV" LeftOf "Default Screen"
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
    InputDevice     "stylus"    "SendCoreEvents"
    InputDevice     "cursor"    "SendCoreEvents"
    InputDevice     "eraser"    "SendCoreEvents"
EndSection

Section "DRI"
    Mode    0666
EndSection
```

---

### Post by oskarloko on 2007-05-20
Talking for the dark side... On WinXp with bootcamp drivers.
When I plug Tv-Out adapter on macbook, no Tv is detected by Intel driver. 
Noi matter what I do, I can't make it work.

I think, as both VGA and S-Video uses the same output; that there's some weird driver option that only OsX can  use...

Keep trying and...

learn francais ??
[http://forum.ubuntu-fr.org/viewtopic.php?id=119824](http://forum.ubuntu-fr.org/viewtopic.php?id=119824)
use gentoo ?
[http://gentoo-wiki.com/Talk:HARDWARE_Apple_MacBook#DVI_and_TV_Out](http://gentoo-wiki.com/Talk:HARDWARE_Apple_MacBook#DVI_and_TV_Out)

Sorry, no clear answers on linux world

---

### Post by Ilove2023 on 2007-05-20
yep... the first link is my post on the french forum... and the little word on the gentoo wiki isn't of great help ;)

I tried the "read-edid" tool and got something weird from the TV :
... for sure, with a "1x1" resolution, it can't be good ;)
```

        # EDID version 1 revision 3
Section "Monitor"
        # Block type: 2:0 3:fc
        Identifier "NTSC/PAL"
        VendorName "APP"
        ModelName "NTSC/PAL"
        # Block type: 2:0 3:fc
        # DPMS capabilities: Active off:yes  Suspend:no  Standby:no

        Mode    "1x1"   # vfreq 38.609Hz, hfreq  9.961kHz
                DotClock        2.570000
                HTimings        1 2 3 258
                VTimings        1 1 18 258
        EndMode
        Mode    "1x1"   # vfreq 38.609Hz, hfreq  9.961kHz
                DotClock        2.570000
                HTimings        1 2 3 258
                VTimings        1 1 18 258
        EndMode
        Mode    "1x1"   # vfreq 38.609Hz, hfreq  9.961kHz
                DotClock        2.570000
                HTimings        1 2 3 258
                VTimings        1 1 18 258
        EndMode
        # Block type: 2:0 3:fc
EndSection

```

The result with VGA adapter :
```

        # EDID version 1 revision 3
Section "Monitor"
        # Block type: 2:0 3:fc
        Identifier "MM904U"
        VendorName "IVM"
        ModelName "MM904U"
        # Block type: 2:0 3:fc
        # Block type: 2:0 3:fd
        HorizSync 30-96
        VertRefresh 50-160
        # Max dot clock (video bandwidth) 200 MHz
        # DPMS capabilities: Active off:yes  Suspend:no  Standby:no

        Mode    "1280x1024"     # vfreq 85.024Hz, hfreq 91.146kHz
                DotClock        157.500000
                HTimings        1280 1344 1504 1728
                VTimings        1024 1025 1028 1072
                Flags   "+HSync" "+VSync"
        EndMode
        Mode    "1024x768"      # vfreq 84.997Hz, hfreq 68.677kHz
                DotClock        94.500000
                HTimings        1024 1072 1168 1376
                VTimings        768 769 772 808
                Flags   "+HSync" "+VSync"
        EndMode
        # Block type: 2:0 3:fc
        # Block type: 2:0 3:fd
EndSection

```

I'll try to have that information from OSX...

---

### Post by Ilove2023 on 2007-05-20
On the apple site web, they say this : 

The cable detect function on pin 25 is implemented by connecting pin 25 to +5V in the adapters. The computer detects which adapter is present by reading its EDID (Extended Display Identification Data) via DDC.** The EDID for video is in the adapter**; the EDID for VGA and DVI is in the display.

So maybe the adapter send bad information on Linux .... ?! ... I guess the Intel driver isn't ready for this adapter....

---

### Post by Ilove2023 on 2007-06-09
If some of you are interested, I reported a bug on freedesktop : [https://bugs.freedesktop.org/show_bug.cgi?id=11211](https://bugs.freedesktop.org/show_bug.cgi?id=11211)

---

