---
title: "how should my xorg.conf look like?"
date: 2007-05-11
forum: Absolute Beginner Talk
---

### Post by bagbiter on 2007-05-11
I've got an NVIDA Go 7400 system in my laptop, so can anyone give me their xorg.conf if you have the same or similar? thanks!

---

### Post by Bachstelze on 2007-05-11
Here's mine, with a fairly similar card :

```
Section "ServerLayout"
        Identifier      "X.org Configured"
        Screen  0       "Screen0"       0       0
        InputDevice     "Mouse"
        InputDevice     "Keyboard"
        InputDevice     "Synaptics Touchpad"
EndSection

Section "Files"
        FontPath        "/usr/share/fonts/misc/"
        FontPath        "/usr/share/fonts/TTF/"
        FontPath        "/usr/share/fonts/OTF"
        FontPath        "/usr/share/fonts/Type1/"
        FontPath        "/usr/share/fonts/CID/"
        FontPath        "/usr/share/fonts/100dpi/"
        FontPath        "/usr/share/fonts/75dpi/"
EndSection

Section "Module"
        Load            "i2c"
        Load            "bitmap"
        Load            "ddc"
        Load            "extmod"
        Load            "freetype"
        Load            "glx"
        Load            "int10"
        Load            "vbe"
EndSection

Section "InputDevice"
        Identifier      "Keyboard"
        Driver          "kbd"
        Option          "CoreKeyboard"
        Option          "XkbLayout"             "fr"
        Option          "XkbModel"              "pc105"
        Option          "XkbVariant"            "latin9"
EndSection

Section "InputDevice"
        Identifier      "Mouse"
        Driver          "mouse"
        Option          "Protocol"              "ImPS/2"
        Option          "Device"                "/dev/input/mice"
        Option          "Emulate3Buttons"       "true"
EndSection

Section "InputDevice"
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        Option          "SendCoreEvents"        "true"
        Option          "Device"                "/dev/psaux"
        Option          "Protocol"              "auto-dev"
        Option          "HorizScrollDelta"      "0"
        Option          "SHMConfig"             "on"
EndSection


Section "Monitor"
        Identifier      "Monitor0"
        HorizSync       28.0 - 64.0
        VertRefresh     43.0 - 60.0
        Option          "DPMS"                  "true"
EndSection

Section "Device"
        Identifier      "Card0"
        Driver          "nvidia"
        Option          "RenderAccel"           "true"
        Option          "AllowGLXWithComposite" "true"
EndSection

Section "Screen"
        Identifier      "Screen0"
        Device          "Card0"
        Monitor         "Monitor0"
        DefaultDepth    24
EndSection

Section "Extensions"
        Option          "Composite"     "Enable"
EndSection

```

---

### Post by bagbiter on 2007-05-11
is this with the newest drivers? the nvidia-glx-new?

---

### Post by Bachstelze on 2007-05-11
I'm not using Ubuntu but yes, this is using the 9755 driver from nvidia.

---

