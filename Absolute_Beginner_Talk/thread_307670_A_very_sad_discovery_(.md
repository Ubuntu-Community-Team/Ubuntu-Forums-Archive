---
title: "A very sad discovery :("
date: 2006-11-26
forum: Absolute Beginner Talk
---

### Post by Hmarroqu on 2006-11-26
i recently upgraded to edgy, everything was going great and i was happy, until....i realized that on my toshiba M55 notebook, the touchpad scrolly thingy was no more!...i used it great on dapper and now on edgy i cant scroll with my touchpad, I HAVE TO DO IT WITH MY ARROW KEYS!:(:( any1 know about this and how to make me happy?

---

### Post by Cardmaster91 on 2006-11-26
OMG, U HAVE TO USE THE ARROW KEYS!!!! 
THATS SO MUCH HARDER AND TAKES ALL OF AN EXTRA  HALF A SECOND


but newys, u might wana check ur macros. just use page up and page down for now tho

---

### Post by ardvark71 on 2006-11-26
> **Cardmaster91 said:**
> OMG, U HAVE TO USE THE ARROW KEYS!!!! 
THATS SO MUCH HARDER AND TAKES ALL OF AN EXTRA  HALF A SECOND


but newys, u might wana check ur macros. just use page up and page down for now tho

I think we could have done without the sarcasm :roll:

---

### Post by adam.tropics on 2006-11-26
Works for me with

```

Section "InputDevice"
   Identifier     "Synaptics Touchpad"
    Driver         "synaptics"
    Option         "SendCoreEvents" "true"
    Option         "Device" "/dev/psaux"
    Option         "Protocol" "auto-dev"
    Option         "HorizScrollDelta" "0"
EndSection
```


edit: should mention, also on Toshiba laptop

---

### Post by towsonu2003 on 2006-11-26
> **Hmarroqu said:**
> i recently upgraded to edgy, everything was going great and i was happy, until....i realized that on my toshiba M55 notebook, the touchpad scrolly thingy was no more!...i used it great on dapper and now on edgy i cant scroll with my touchpad, I HAVE TO DO IT WITH MY ARROW KEYS!:(:( any1 know about this and how to make me happy?

Could you post your /etc/X11/xorg.conf ? maybe we can find something useful there?

Edit: I was slow :) see above post [http://ubuntuforums.org/showpost.php?p=1812015&postcount=4](http://ubuntuforums.org/showpost.php?p=1812015&postcount=4)

> **ardvark71 said:**
> I think we could have done without the sarcasm :roll:

+1

---

### Post by Hmarroqu on 2006-11-27
> 
Section "Files"
    FontPath    "/usr/share/X11/fonts/misc"
    FontPath    "/usr/share/X11/fonts/cyrillic"
    FontPath    "/usr/share/X11/fonts/100dpi/:unscaled"
    FontPath    "/usr/share/X11/fonts/75dpi/:unscaled"
    FontPath    "/usr/share/X11/fonts/Type1"
    FontPath    "/usr/share/X11/fonts/100dpi"
    FontPath    "/usr/share/X11/fonts/75dpi"
    # path to defoma fonts
    FontPath    "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
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
    Identifier    "Generic Keyboard"
    Driver        "kbd"
    Option        "CoreKeyboard"
    Option        "XkbRules"    "xorg"
    Option        "XkbModel"    "pc104"
    Option        "XkbLayout"    "us"
EndSection

Section "InputDevice"
    Identifier    "Configured Mouse"
    Driver        "mouse"
    Option        "CorePointer"
    Option        "Device"        "/dev/input/mice"
    Option        "Protocol"        "ExplorerPS/2"
    Option        "ZAxisMapping"        "4 5"
    Option        "Emulate3Buttons"    "true"
EndSection

Section "InputDevice"
    Identifier    "Synaptics Touchpad"
    Driver        "synaptics"
    Option        "SendCoreEvents"    "true"
    Option        "Device"        "/dev/psaux"
    Option        "Protocol"        "auto-dev"
    Option        "HorizScrollDelta"    "0"
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
    Identifier    "Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller"
    Driver        "i810"
    BusID        "PCI:0:2:0"
EndSection

Section "Monitor"
    Identifier    "Generic Monitor"
    Option        "DPMS"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Device        "Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller"
    Monitor        "Generic Monitor"
    DefaultDepth    24
    SubSection "Display"
        Depth        1
        Modes        "1280x768"
    EndSubSection
    SubSection "Display"
        Depth        4
        Modes        "1280x768"
    EndSubSection
    SubSection "Display"
        Depth        8
        Modes        "1280x768"
    EndSubSection
    SubSection "Display"
        Depth        15
        Modes        "1280x768"
    EndSubSection
    SubSection "Display"
        Depth        16
        Modes        "1280x768"
    EndSubSection
    SubSection "Display"
        Depth        24
        Modes        "1280x768"
    EndSubSection
EndSection

Section "ServerLayout"
    Identifier    "Default Layout"
    Screen        "Default Screen"
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
    InputDevice     "stylus" "SendCoreEvents"
    InputDevice     "cursor" "SendCoreEvents"
    InputDevice     "eraser" "SendCoreEvents"
    InputDevice    "Synaptics Touchpad"
EndSection

Section "DRI"
    Mode    0666
EndSectioni have no idea what is going on there and also i should mention that there is another xorg.conf.20061124063507  that date 20061124 is when i upgraded to edgy...so....?

PS/ i think i should mention that my usb wireless mouse works fine with the scrolling..

---

### Post by towsonu2003 on 2006-11-27
Well, you could post that older xorg.conf and we (or you) could check if there is aything different with the new one. In the meantime,

You see this part in your xorg.conf:
```

Section "InputDevice"
   Identifier     "Synaptics Touchpad"
    Driver         "synaptics"
    Option         "SendCoreEvents" "true"
    Option         "Device" "/dev/psaux"
    Option         "Protocol" "**auto-dev**"
    Option         "HorizScrollDelta" "0"
EndSection

```

First, try changing it to this and restart X:
```

Section "InputDevice"
   Identifier     "Synaptics Touchpad"
    Driver         "synaptics"
    Option         "SendCoreEvents" "true"
    Option         "Device" "/dev/psaux"
    Option         "Protocol" "**PS2**"
    Option         "HorizScrollDelta" "0"
EndSection

```

If that doesn't work, try to change it to this and restart X:
```

Section "InputDevice"
   Identifier "Synaptics Touchpad"
    Driver "mouse"
    Option "CorePointer"
    Option "Device" "/dev/psaux"
    Option "Protocol" "PS/2"
    Option "Emulate3Buttons" "true"
EndSection

```

but before doing that, pls **[SIZE="4"]backup[/SIZE]** your existing xorg.conf and be careful with the commands you issue ;) 

I found the above section here: [http://linux.toshiba-dme.co.jp/linux/eng/pc/memo2/satM40.htm](http://linux.toshiba-dme.co.jp/linux/eng/pc/memo2/satM40.htm)

If either of these work, I would file a bug report to [launchpad.net]("https://bugs.launchpad.net/distros/ubuntu/+source/xorg/+filebug").

---

### Post by Hmarroqu on 2006-11-27
replacing the "auto-dev" to "PS2" worked! thank you lots!

---

### Post by towsonu2003 on 2006-11-27
> **Hmarroqu said:**
> replacing the "auto-dev" to "PS2" worked! thank you lots!

you're most welcome. I'd file a bug report if I were you :)

---

### Post by Hmarroqu on 2006-11-28
the problem came back unfortunately. i edited both of those files with the same "PS2" it worked with the first file, then after a restart it stoped so i edited the second file, that worked as well, but now it doesnt work at all after the 3rd time using my comp and i have no idea as to why!?!?

---

### Post by towsonu2003 on 2006-12-12
> **Hmarroqu said:**
> the problem came back unfortunately. i edited both of those files with the same "PS2" it worked with the first file, then after a restart it stoped so i edited the second file, that worked as well, but now it doesnt work at all after the 3rd time using my comp and i have no idea as to why!?!?

try restarting X only. it might be [this bug]("https://launchpad.net/distros/ubuntu/+source/xserver-xorg-input-synaptics/+bug/69152").

---

### Post by tempest152 on 2006-12-12
If all else fails and the touch mouse pad wont work, get a cheap USB mouse, would be ok for home use, but on the road might not be as efficient.

---

