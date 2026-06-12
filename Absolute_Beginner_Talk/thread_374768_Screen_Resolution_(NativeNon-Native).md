---
title: "Screen Resolution (Native/Non-Native?)"
date: 2007-03-02
forum: Absolute Beginner Talk
---

### Post by andou on 2007-03-02
I've got a U-Plus Vision 30" Monitor, which the sales guy 'said' has native 2560x1600 resolution. In Windows, I had to un-check "Hide resolutions that this monitor doesn't support" in display settings to get it to work, but after that it was fine.

I've tried playing around with the xorg.conf file and finally checked Modeline, after finding this[howto guide]("http://gentoo-wiki.com/HOWTO_Widescreen_Resolutions_(WSXGA)").

Here's what it says:
```
(WW) NVIDIA(0): Mode "1400x1050" is too large for UPV UP-M30W1 (DFP-0);
(WW) NVIDIA(0):     discarding.
(WW) NVIDIA(0): Mode "1440x900" is too large for UPV UP-M30W1 (DFP-0);
(WW) NVIDIA(0):     discarding.
(WW) NVIDIA(0): Mode "1600x1024" is too large for UPV UP-M30W1 (DFP-0);
(WW) NVIDIA(0):     discarding.
(WW) NVIDIA(0): Mode "1680x1050" is too large for UPV UP-M30W1 (DFP-0);
(WW) NVIDIA(0):     discarding.
(WW) NVIDIA(0): Mode "1920x1200" is too large for UPV UP-M30W1 (DFP-0);
(WW) NVIDIA(0):     discarding.
(WW) NVIDIA(0): Mode "1280x960" is too large for UPV UP-M30W1 (DFP-0);
(WW) NVIDIA(0):     discarding.
(WW) NVIDIA(0): Mode "1280x1024" is too large for UPV UP-M30W1 (DFP-0);
(WW) NVIDIA(0):     discarding.
(WW) NVIDIA(0): Mode "1600x1200" is too large for UPV UP-M30W1 (DFP-0);
(WW) NVIDIA(0):     discarding.
(II) NVIDIA(0): Assigned Display Device: DFP-0
(WW) NVIDIA(0): No valid modes for "1680x1050"; removing.
(WW) NVIDIA(0): No valid modes for "2650x1600"; removing.
```

Obviously, the resolution I'm trying to get is "too large for the UPV UP -M30W1" It works in Windows, and having 1280x800 resolution on a 30" monitor is really frustrating. Is it possible to get 2560x1600? Thanks in advance for the help.

Oh, by the way, I've got an XFX GeForce 7900gt v430 and have Ubuntu 6.10 installed.

---

### Post by o_fortuna on 2007-03-03
The next thing to try is to press Alt+F2 and run
```
nvidia-settings
```
(this will work if you are using nvidia proprietary drivers) You can select the resolution from the second selection down, but it might not work.

I don't know if modelines really work well anymore, but ; but there still might be a way to save it. If you can find documentation for your monitor (either the manual that came with it or the manufacturers' website), you can get the horizontal and vertical refresh rates. Actually putting  those in there might help:
```
    HorizSync       30.0 - 83.0
    VertRefresh     56.0 - 75.0
```
Only with your rates in there instead of mine :) Also, try changing the resolution on these lines (under screen):
```
    SubSection     "Display"
        Depth       24
        Modes      "1280x1024" "1024x768" "800x600" "720x400" "640x480"
    EndSubSection
```
substituting your own resolutions. Again, I don't "know" if this will work. But it's something to try, at least.

---

### Post by andou on 2007-03-03
Thanks for the great suggestions. Unfortunately, none of them worked.

I didn't see any resolution settings in the nvidia-settings pannel. I tried playing around more with the xorg.conf file, but couldn't get anything higher than 1280x800.

I figure, if Windows can do it, there's got to be a way... of course, I'm totally newb and my guesses are pretty worthless. So, that leaves me with only hope - which I've still got :D

---

### Post by andou on 2007-03-03
Thanks for the great suggestions. Unfortunately, none of them worked.

I didn't see any resolution settings in the nvidia-settings pannel. I tried playing around more with the xorg.conf file, but couldn't get anything higher than 1280x800.

I figure, if Windows can do it, there's got to be a way... of course, I'm totally newb and my guesses are pretty worthless. So, that leaves me with only hope - which I've still got :D

What now?

---

### Post by Aliarse on 2007-03-03
If that didn't work, you could try the method i used to get my naitive res working for my widescreen.

[http://ubuntuforums.org/showthread.php?p=2232359#post2232359](http://ubuntuforums.org/showthread.php?p=2232359#post2232359)

Last post. HTH. Nice monitor btw, im green.

---

### Post by andou on 2007-03-03
Thanks for the reply.

Ok, I tried ```
gtf 2560 1600 60
```
And this is what came out: ```
  # 2560x1600 @ 60.00 Hz (GTF) hsync: 99.36 kHz; pclk: 348.16 MHz
  Modeline "2560x1600_60.00"  348.16  2560 2752 3032 3504  1600 1601 1604 1656  -HSync +Vsync 
```

So, I put it in my xorg.conf file in the monitor settings. I'm guessing that it's just the modeline, as the other part seems to be commented out, but I just left it as is. I'll try uncommenting that other part...

Anyway... still no dice.

Any other suggestions?

---

### Post by Aliarse on 2007-03-03
If you mean my post, i never had to uncomment it.

Just restarted X and then selected my newly available res in the screen resolution options.

---

### Post by andou on 2007-03-03
Definitely not a good idea to uncomment that.

Hmm. What next?

---

### Post by Aliarse on 2007-03-03
Did you do all of the post in that thread, and it still didnt work?

If so, im out of ideas for you man.

---

### Post by andou on 2007-03-03
> **Aliarse said:**
> Did you do all of the post in that thread, and it still didnt work?

If so, im out of ideas for you man.

Yeah, I did. I liked your ideas, and I really appreciate the help. It didn't work for me... but it was a good effort. Thanks for you help :)

Anyway... still got to figure this out then.

---

### Post by andou on 2007-03-04
Well, I tried reinstalling the nvidia driver, searched google for a couple hours, and repeated the steps again and again.

nothing.

starting to get a bit bummed out.

---

### Post by andou on 2007-03-04
pretty bummed out about it now.

---

### Post by andou on 2007-03-06
Totally bummed out about the resolution issue now... giving up on it. Maybe I'll figure it out one day... but I can't just spend all day everyday banging my head against a wall and getting nowhere.

On to other things.

Thanks for the ideas though :D

---

### Post by andou on 2007-04-23
Still no solution....

---

### Post by andou on 2007-07-29
Ok, 

So, I'm trying this again... Still no dice.

I tried /var/log/Xorg.0.log And this is what I'm looking at:
```
(--) NVIDIA(0): UPV UP-M30W1 (DFP-0): Internal Dual Link TMDS
(WW) NVIDIA(0): Mode "1280x960" is too large for UPV UP-M30W1 (DFP-0);
(WW) NVIDIA(0):     discarding.
(WW) NVIDIA(0): Mode "1280x1024" is too large for UPV UP-M30W1 (DFP-0);
(WW) NVIDIA(0):     discarding.
(WW) NVIDIA(0): Mode "1600x1200" is too large for UPV UP-M30W1 (DFP-0);
(WW) NVIDIA(0):     discarding.
(WW) NVIDIA(0): Mode "1400x1050" is too large for UPV UP-M30W1 (DFP-0);
(WW) NVIDIA(0):     discarding.
(WW) NVIDIA(0): Mode "1440x900" is too large for UPV UP-M30W1 (DFP-0);
(WW) NVIDIA(0):     discarding.
(WW) NVIDIA(0): Mode "1600x1024" is too large for UPV UP-M30W1 (DFP-0);
(WW) NVIDIA(0):     discarding.
(WW) NVIDIA(0): Mode "1680x1050" is too large for UPV UP-M30W1 (DFP-0);
(WW) NVIDIA(0):     discarding.
(WW) NVIDIA(0): Mode "1920x1200" is too large for UPV UP-M30W1 (DFP-0);
(WW) NVIDIA(0):     discarding.
(WW) NVIDIA(0): Mode "1280x960" is too large for UPV UP-M30W1 (DFP-0);
(WW) NVIDIA(0):     discarding.
(WW) NVIDIA(0): Mode "1280x1024" is too large for UPV UP-M30W1 (DFP-0);
(WW) NVIDIA(0):     discarding.
(WW) NVIDIA(0): Mode "1600x1200" is too large for UPV UP-M30W1 (DFP-0);
(WW) NVIDIA(0):     discarding.
(II) NVIDIA(0): Assigned Display Device: DFP-0
(II) NVIDIA(0): Validated modes:
(II) NVIDIA(0):     "1280x800"
(II) NVIDIA(0): Virtual screen size determined to be 1280 x 800
(--) NVIDIA(0): DPI set to (40, 45); computed from "UseEdidDpi" X config option
(--) Depth 24 pixmap format is 32 bpp

```

With XP, I had to uncheck the "hide modes this monitor doesn't display" box in display settings. With Vista, it shows 2560x1600 as the native resolution. Any ideas... anyone?

---

### Post by tredegar on 2007-07-31
andou,
I have posted a possible solution for you in the thread you started about this problem over on LQ. Here:
[http://www.linuxquestions.org/questions/showthread.php?p=2841717#post2841717](http://www.linuxquestions.org/questions/showthread.php?p=2841717#post2841717)

---

### Post by razeshkale on 2007-07-31
google for Custamise screen resolution in ubuntu

---

### Post by MrHippocampus on 2007-07-31
Please post your /etc/X11/xorg.conf, youll need to edit that since your montior is clearly not reporting its possible resolutions correctly.

---

### Post by andou on 2007-07-31
Here's my /etc/X11/xorg.conf:
```
[Section "Screen"
    Identifier     "Default Screen"
    Device         "NVIDIA Corporation NVIDIA Default Card"
    Monitor        "UP-M30W1"
    DefaultDepth    24
    Option         "UseEdid" "True"
    Option         "NoLogo" "True"
    SubSection     "Display"
        Virtual     1280 800
        Depth       1
        Modes      "1280x800"
    EndSubSection
    SubSection     "Display"
        Virtual     1280 800
        Depth       4
        Modes      "1280x800"
    EndSubSection
    SubSection     "Display"
        Virtual     1280 800
        Depth       8
        Modes      "1280x800"
    EndSubSection
    SubSection     "Display"
        Virtual     1280 800
        Depth       15
        Modes      "1280x800"
    EndSubSection

```

And here's a nvidia-xconfig --query-gpu-info:
```
[Number of GPUs: 1

GPU #0:
  Name      : GeForce 7900 GT/GTO
  PCI BusID : PCI:5:0:0

  Number of Display Devices: 1

  Display Device 0 (DFP-0):
     EDID Name             : UPV UP-M30W1
     Minimum HorizSync     : 30.000 kHz
     Maximum HorizSync     : 80.000 kHz
     Minimum VertRefresh   : 59 Hz
     Maximum VertRefresh   : 61 Hz
     Maximum PixelClock    : 268.500 MHz
     Maximum Width         : 2560 pixels
     Maximum Height        : 1600 pixels
     Preferred Width       : 1280 pixels
     Preferred Height      : 800 pixels
     Preferred VertRefresh : 60 Hz
     Physical Width        : 800 mm
     Physical Height       : 450 mm
```
I'm not sure what to do... but I'm pretty sure there's a way, if this is showing that the Max WidthxHeight is 2560x1600.

---

### Post by MrHippocampus on 2007-07-31
Sorry but you'll need to post your entire xorg.conf as sometimes you need to edit more than one section to get things working nicely :)

---

### Post by jimbob on 2007-07-31
You are calling for a default depth of 24 but it isn't listed.  Try changing all of the 1280x800 to 2560x1600 to force it.   Only list the depth of 24, those others aren't necessary.  Also take those virtual 1280 800 lines out of there.  Here is my screen section:

Section "Screen"
        Identifier "Screen0"
        Device     "Card0"
        Monitor    "Monitor0"
        DefaultDepth    24
        Option         "AddARGBGLXVisuals" "true"
        Option         "NvAGP" "3"  # this only for display connected to a card in an AGP slot
        Option         "Accel" "true"
        Option         "RenderAccel" "true"
        Option         "AllowGLXWithComposite" "true"   # if not using compositing set to "false"
        Option         "XAANoOffscreenPixmaps" "true"
        Option         "DigitalVibrance" "0"
        Option         "Overlay" "true"
        Option         "CIOverlay" "true"
        Option         "TransparentIndex" "60"
        Option         "OverlayDefaultVisual" "false"
        Option         "SWCursor" "false"
        Option         "HWCursor" "true"
        Option         "CursorShadow" "off"
        Option         "CursorShadowAlpha" "64"
        Option         "CursorShadowXOffset" "4"
        Option         "CursorShadowYOffset" "2"
        Option         "metamodes"  "nvidia-auto-select +0+0"
        SubSection "Display"
                Depth           24
                Modes           "1920x1200" 
        EndSubSection


________________________________       
  If I can't be Mr. Root I won't play ...

[COLOR="Red"][SIZE="1"]*Registered Linux User #400396*[/SIZE][/COLOR]

... things should be done from the command line the way Nature intended ...

---

### Post by andou on 2007-08-01
Thanks for the advice... I'll try that out and see how it goes....

---

### Post by andou on 2007-08-01
Made a mistake with my post... tried to press back, but that didn't work. oops.

---

### Post by andou on 2007-08-01
Here's my xorg.conf:

```

# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder3)  Fri Dec 15 10:12:14 PST 2006

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
    FontPath        "/usr/share/X11/fonts/misc"
    FontPath        "/usr/share/X11/fonts/cyrillic"
    FontPath        "/usr/share/X11/fonts/100dpi/:unscaled"
FontPath        "/usr/share/X11/fonts/75dpi/:unscaled"
    FontPath        "/usr/share/X11/fonts/Type1"
    FontPath        "/usr/share/X11/fonts/100dpi"
    FontPath        "/usr/share/X11/fonts/75dpi"
    FontPath        "/usr/share/fonts/X11/misc"
    FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
    Load           "i2c"
    Load           "bitmap"
    Load           "ddc"
    Load           "extmod"
    Load           "freetype"
    Load           "glx"
    Load           "int10"
    Load           "type1"
    Load           "vbe"
EndSection

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "CoreKeyboard"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc105"
    Option         "XkbLayout" "us"
    Option         "XkbOptions" "lv3:ralt_switch"
EndSection

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ExplorerPS/2"
    Option         "ZAxisMapping" "4 5"
    Option         "Emulate3Buttons" "true"
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
    Identifier     "stylus"
    Driver         "wacom"
    Option         "Device" "/dev/wacom"          # Change to
    Option         "Type" "stylus"
    Option         "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
    Identifier     "eraser"
    Driver         "wacom"
    Option         "Device" "/dev/wacom"          # Change to
    Option         "Type" "eraser"
    Option         "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
 Identifier     "cursor"
    Driver         "wacom"
    Option         "Device" "/dev/wacom"          # Change to
    Option         "Type" "cursor"
    Option         "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "Monitor"
    Identifier     "UP-M30W1"
    Option         "DPMS"
    HorizSync      30-80
    VertRefresh    59-61
EndSection

Section "Device"
    Identifier     "NVIDIA Corporation NVIDIA Default Card"
    Driver         "nvidia"
    Option "UseEdidFreqs" "FALSE"
    Option "UseEdidDpi" "TRUE"
#    Option "ModeValidation" "NoEdidModes"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "NVIDIA Corporation NVIDIA Default Card"
    Monitor        "UP-M30W1"
    DefaultDepth    24
#    Option         "UseEdid" "True"
    Option         "NoLogo" "True"
    SubSection     "Display"
        Depth       24
        Modes      "2560x1600" "1280x800" "1280x768" "1200x800" "1024x768" "800x600"
    EndSubSection
Modes      "2560x1600" "1280x800" "1280x768" "1200x800" "1024x768" "800x600"
    EndSubSection
  EndSection

Section "Extensions"
    Option         "Composite" "Enable"
EndSection

```

I commented out Option "ModeValidation" "NoEdidModes" because, I couldn't see anything but a black screen after reboot with it in. Anyway... still running at 1280x800...

---

### Post by responder on 2007-12-04
Hi Folks,

Any ideas where i can get my hands on one of these monitors? many thanks

---

