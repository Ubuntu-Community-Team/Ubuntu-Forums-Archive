---
title: "[SOLVED] Trying to Get Compiz Running on my Intel 910GL graphics chipset."
date: 2007-10-25
forum: Absolute Beginner Talk
---

### Post by DaGrimReefah on 2007-10-25
Hello. I've been at this for a while and have found no relevant help in these here forums. Here is my xorg.conf:

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
        Identifier      "Intel Corporation 82915G/GV/910GL Integrated Graphics Controller"
        Driver          "intel"
        BusID           "PCI:0:2:0"
        Option          "AddARGBGLXVisuals"     "True"
        Option          "AllowGLXWithComposite" "True"
EndSection

Section "Monitor"
        Identifier      "DELL E173FP"
        Option          "DPMS"
        HorizSync       31-80
        VertRefresh     56-75
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "Intel Corporation 82915G/GV/910GL Integrated Graphics Controller"
        Monitor         "DELL E173FP"
        DefaultDepth    16
        SubSection "Display"
                Modes           "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
        EndSubSection
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

And here is what happens when I type "compiz" in the terminal: 
 ```
Checking for Xgl: not present. 
Detected PCI ID for VGA: 00:02.0 0300: 8086:2582 (rev 04) (prog-if 00 [VGA])
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: not present. 
SKIP_CHECKS is yes, so continuing despite problems.
Checking for nVidia: not present. 
Checking for FBConfig: Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
not present. 
SKIP_CHECKS is yes, so continuing despite problems.
Checking for Xgl: not present. 
Starting emerald
Xlib:  extension "GLX" missing on display ":0.0".
Window manager warning: "" found in configuration database is not a valid value for keybinding "toggle_shaded"

```

...and when I type "glxinfo":

```
name of display: :0.0
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x21 16 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x22 16 dc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x47 32 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None

```

Help?

---

### Post by mikeyphi on 2007-10-25
Open Systen/Administration/Screens & Graphics - check your graphics driver. You might want to check, if it's not nvidia-gxl-new, that you can use nvidia-gxl-new

---

### Post by Whiffle on 2007-10-25
Except he doesn't have an nvidia graphics card so that won't help...


Strangely enough I have the same chipset on my T43 and compiz worked right out of the box, here is my Xorg.conf

[http://www.resnet.trinity.edu/avaselaa/xorg.conf.txt](http://www.resnet.trinity.edu/avaselaa/xorg.conf.txt)

---

### Post by DaGrimReefah on 2007-10-25
It says I have "i810" drivers, but then it has another section underneath it that says generic vesa drivers. I don't know which one is correct. However, I have my Ubuntu on an external and I switch from my NVIDIA PC at home (which works great) to my intel 910GL PC at school. Restricted driver manager doesn't even show my Nvidia driver on it when it's connected at school.

---

### Post by Whiffle on 2007-10-25
Ahh thats your problem. You need 2 xorgs, one for when you're using your nvidia and one for your intel, the configurations between the two aren't compatable.

---

### Post by Whiffle on 2007-10-25
Or, you could possibly setup two different Devices in your one xorg.conf and force it to always load the drivers for both, which might take some fanagaling but I think it could work.

---

### Post by DaGrimReefah on 2007-10-25
How do I make another xorg?

---

### Post by DaGrimReefah on 2007-10-25
I reviewed my xorg.conf thoroughly, and have found that 2 xorgs are not needed, as the xserver automatically configures itself to your hardware. You just simply have to change the drivers accordingly. I'm using the ubuntu-provided intel driver, and I've already tried the i810 driver. Do I need to install the latest unrestricted driver? If so, can someone give me a how-to link?

---

### Post by DaGrimReefah on 2007-10-25
Srry for the multiple posts. But I guess what I'm really asking is... do I need to activate GLX for this intel chipset, and if so, how?

---

### Post by DaGrimReefah on 2007-10-25
Hello? Anyone?

Helpful forums here... Sarcasm...

Instead of helping, I just get labeled. Spilled the beans means nothing to me, but I would appreciate if that moderator who took the troubles to label me (in a futile attempt to vindicate his/her obviously feeble ego) would maybe give me a tip relating to the subject of this thread. Thanks.

---

