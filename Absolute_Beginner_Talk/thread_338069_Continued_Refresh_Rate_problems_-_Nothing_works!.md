---
title: "Continued Refresh Rate problems - Nothing works!"
date: 2007-01-13
forum: Absolute Beginner Talk
---

### Post by Amadeo on 2007-01-13
I was able to install the latest Nvidia 97.46 drivers for my 6600 GT.  All of the resolutions show up properly within Gnome, but my refresh rate can go no higher than 75Hz at 1280x1024.  My monitor does support higher.  Other (lower) resolutions show a max of 60Hz.  

I've edited my xorg.conf to adjust the monitor horizontal and vertical frequencies, but I am still unable to change my refresh rate within Gnome.  I've also used dpkg-reconfigure xserver-xorg, but this actually just made it worse, so I reverted to my xorg.conf backup.

The strange thing is, the NVIDIA X Server Settings program lists resolutions that aren't defined in my xorg.conf file.  It also displays more information, such as the make of my monitor - this is also not in my xorg.conf file.  Unfortunately, I don't believe it allows me to define the correct frequencies or refresh rates that my monitor supports.

I do have an older monitor, it is a Hitachi SuperScan Elite 802, or CM802U.  The monitor has a vertical frequency range of 31-100Hz and a horizontal range of 50-160Hz.  I'm at the point where I honestly don't know what to do next!  I'd appreciate any and all help.

default xorg.conf:
Note: I've tried changing the values to 31 - 100 and 50 - 160, but here's the default file now.

```

Section "Monitor"
    Identifier     "Generic Monitor"
    HorizSync       28.0 - 64.0
    VertRefresh     43.0 - 60.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "NVIDIA Corporation NV43 [GeForce 6600/GeForce 6600 GT]"
    Driver         "nvidia"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "NVIDIA Corporation NV43 [GeForce 6600/GeForce 6600 GT]"
    Monitor        "Generic Monitor"
    DefaultDepth    24
    SubSection     "Display"
        Depth       1
        Modes      "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
EndSection 
```

Xorg.0.log:
Note: I can select more resolutions than shown here within Gnome.

```
(II) Setting vga for screen 0.
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Enabling RENDER acceleration
(II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) NVIDIA(0):     enabled.
(II) NVIDIA(0): NVIDIA GPU GeForce 6600 GT at PCI:1:0:0 (GPU-0)
(--) NVIDIA(0): Memory: 131072 kBytes
(--) NVIDIA(0): VideoBIOS: 05.43.02.46.68
(II) NVIDIA(0): Detected AGP rate: 4X
(--) NVIDIA(0): Interlaced video modes are supported on this GPU
(--) NVIDIA(0): Connected display device(s) on GeForce 6600 GT at PCI:1:0:0:
(--) NVIDIA(0):     Hitachi (CRT-0)
(--) NVIDIA(0): Hitachi (CRT-0): 400.0 MHz maximum pixel clock
(II) NVIDIA(0): Assigned Display Device: CRT-0
(WW) NVIDIA(0): No valid modes for "720x400"; removing.
(II) NVIDIA(0): Validated modes:
(II) NVIDIA(0):     "1280x1024"
(II) NVIDIA(0):     "1024x768"
(II) NVIDIA(0):     "832x624"
(II) NVIDIA(0):     "800x600"
(II) NVIDIA(0):     "640x480"
(II) NVIDIA(0): Virtual screen size determined to be 1280 x 1024
(--) NVIDIA(0): DPI set to (81, 86); computed from "UseEdidDpi" X config
(--) NVIDIA(0):     option
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
```

---

### Post by Amadeo on 2007-01-14
I have a feeling this isn't a favorite topic of people in the know. :mrgreen:

---

### Post by floke on 2007-01-14
Your xorg.conf settings show that the monitor being used is a 'generic monitor'. This means that ubuntu hasn't automatically detected it. You need to edit the file and change the entries to 'generic monitor' to whatever monitor it is you have. You then need to change/add the appropriate refresh rates, which you seem to know already.

(don't know how to enter refresh rates into an xorg.conf file though, so I'd have a google / forum wander on this one)

Remember to make a copy of your xorg.conf file before you make any changes in case something gets screwed up. 

To edit and change the file enter: sudo nano /etc/X11/xorg.conf
Ctrl-X to exit, select 'y' to save on exiting.

Before doing this, though (and if anything goes drastically wrong int he future), you might want to try

sudo dpkg-reconfigure -phigh xserver-xorg

to set it up your xorg files again

Hope this is of some help

---

### Post by Amadeo on 2007-01-14
That's the problem...doing that stuff doesn't work. :(

Example, here's my current xorg.conf file:
```

Section "Monitor"
    Identifier     "CM802U"
    HorizSync       31.0 - 100.0
    VertRefresh     50.0 - 160.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "NVIDIA Corporation NV43 [GeForce 6600/GeForce 6600 GT]"
    Driver         "nvidia"
    Option         "NoLogo"
EndSection

Section "Screen"
    Identifier     "CM802U"
    Device         "NVIDIA Corporation NV43 [GeForce 6600/GeForce 6600 GT]"
    Monitor        "CM802U"
    DefaultDepth    24
    SubSection     "Display"
        Depth       1
        Modes      "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
EndSection
```

However, after an X restart, I'm only able to choose 55Hz now under Gnome's Screen Resolution.  There are also 7 other resolutions there that are not defined in this file.

If I go into the NVIDIA X Server Settings, there are 24 more resolutions to choose from, and I'm able to choose a maximum of 75Hz for 1280x1024.  Other resolutions show a max of 50 or 60Hz.  

Unless I'm doing something wrong, none of this editing or reconfiguring is working. :(

---

### Post by floke on 2007-01-14
To be honest, this has worked for me in the past, so i have no experience of having to edit things further. Sorry not to be of more help, but if the monitor can support the higher refresh rates etc. then you will be able to get it to work, it's just knowing how to do it that's the problem (as always). 

Perhaps someone with more experience of this can lend a hand....?

---

### Post by Amadeo on 2007-01-14
Well, after 3-4 days and lots of attempts to resolve this, I came across a Gentoo user who was able to find the solution:


Adding:
```
Option "UseEdidFreqs" "false" 
```
To the device section will allow you to select the correct frequencies from within the NVIDIA X Server Settings.

Gnome's Screen Resolution will still display incorrect refresh rates and/or resolutions.  I believe you can fix this by adding:

```
Option "DynamicTwinView" "0"
```
To the same device section.  Not positive on that, but I'm happy with how it works right now. :)

---

### Post by floke on 2007-01-14
Glad to hear you got it sorted.
I came across this in the HowTo's list, which might be useful

[http://ubuntuforums.org/showthread.php?t=83973](http://ubuntuforums.org/showthread.php?t=83973)

Still, at least it works now!

---

