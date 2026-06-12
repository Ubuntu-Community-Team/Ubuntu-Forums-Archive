---
title: "Toshiba Laptop and Synaptics touchpad"
date: 2007-04-21
forum: Absolute Beginner Talk
---

### Post by hoopvillian on 2007-04-21
My Synaptics touchpad isn't being recognized at all on my Toshiba laptop.  Its a A105 series.  It's not showing up in the xorg file even though I installed, and reinstalled it.  I tried installing qsynaptic but it didn't help.

---

### Post by Bachstelze on 2007-04-21
You mean that when you "touch" it, the pointer doesn't move or that you can't use it's advanced features like tapping and scrolling ?

---

### Post by hoopvillian on 2007-04-21
Basic features work, and I can use some advanced features like tapping, but scrolling doesn't work at all.  In my xorg.conf file there is no mention of synaptics touchpad anywhere, and even when I manually tried to add it, id didn't recognize it.

---

### Post by Bachstelze on 2007-04-21
OK, here's my xorg.conf as an example :

```

Section "ServerLayout"
        Identifier      "X.org Configured"
        Screen  0       "Screen0"       0       0
        InputDevice     "Mouse"
        InputDevice     "Keyboard"
        InputDevice     "Synaptics Touchpad"
EndSection

Section "Files"
        RgbPath         "/usr/share/X11/rgb"
        ModulePath      "/usr/lib/xorg/modules"
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

The parts that interest us are the ones about the touchpad. First, the InputDevice section about it :

```

Section "InputDevice"
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        Option          "SendCoreEvents"        "true"
        Option          "Device"                "/dev/psaux"
        Option          "Protocol"              "auto-dev"
        Option          "HorizScrollDelta"      "0"
        Option          "SHMConfig"             "on"
EndSection

```

copy those lines in yours. Xorg will then know about your touchpad but will *not* use it. To tell Xorg you want to use the touchpad, you add a line about it in the ServerLayout section :

```

Section "ServerLayout"
        [...]
        InputDevice     "Synaptics Touchpad"
EndSection

```

Note that the secont argument on the line is the same as the "Identifier" argument we used just before, you can change it to something else if you wish. Then all you need to do is to restart X with

```
sudo /etc/init.d/gdm restart
```

and voilà, your touchpad should be fully operational.

---

### Post by Episcopus on 2007-04-22
**HymnToLife**

Your instructions helped me get my synaptics touchpad working right, thanks.  Do you know how to configure the touchpad further?  I would like to use click locking and customizable zones if I can.

---

### Post by cstrippie on 2007-04-22
Open add/remove and type "synaptic" in the search bar - there is a graphical synaptic configuration tool in there that I use (quite successfully).  You may need to add a line to your X11 config, but the driver will tell you what is needed.

---

### Post by hoopvillian on 2007-04-22
THANK YOU HymnToLife.  Worked.  Much appreciated.

---

