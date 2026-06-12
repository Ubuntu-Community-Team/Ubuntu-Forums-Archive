---
title: "Video mode not supported at gdm/login window"
date: 2008-01-05
forum: Absolute Beginner Talk
---

### Post by oliviacond on 2008-01-05
But I can hear the "log-in drums" in the background, and blindly type in my username and hit enter, then blindly type in my password, I hear the "log-in success" drums and the graphics come back and all seems OK.

my xorg:
```

Section "Files"
        Fontpath        "/usr/share/fonts/X11/misc"
        Fontpath        "/usr/share/fonts/X11/cyrillic"
        Fontpath        "/usr/share/fonts/X11/100dpi/:unscaled"
        Fontpath        "/usr/share/fonts/X11/75dpi/:unscaled"
        Fontpath        "/usr/share/fonts/X11/Type1"
        Fontpath        "/usr/share/fonts/X11/100dpi"
        Fontpath        "/usr/share/fonts/X11/75dpi"
        # path to defoma fonts
        Fontpath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
        Load            "i2c"
        Load            "bitmap"
        Load            "ddc"
        Load            "dri"
        Load            "extmod"
        Load            "freetype"
        Load            "glx"
        Load            "int10"
        Load            "vbe"
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
        Identifier      "ATI Technologies Inc RV350 AP [Radeon 9600]"
        Driver          "fglrx"
        BusID           "PCI:1:0:0"
        Option          "UseFBDev"              "true"
        Option          "UseFastTLS" "2"
EndSection

Section "Extensions"
        Option          "Composite"     "0"
EndSection

Section "Monitor"
        Identifier      "SyncMaster"
        Option          "DPMS"
        HorizSync       30-61
        VertRefresh     56-75
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "ATI Technologies Inc RV350 AP [Radeon 9600]"
        Monitor         "SyncMaster"
        DefaultDepth    24
        SubSection "Display"
                Modes           "1280x1024" "1024x768" "800x600" "640x480"
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

Section "DRI"
        Mode    0666
EndSection

```

---

### Post by geirha on 2008-01-05
What model is your monitor? My guess is that the HorizSync and VertRefresh options of your monitor section is not completely correct for your monitor. Commenting out those lines might work, as X then would try to detect those values itself (this has worked for most monitors I've encountered). 
```
Section "Monitor"
        Identifier      "SyncMaster"
        Option          "DPMS"
        [color=blue]#[/color] HorizSync       30-61
        [color=blue]#[/color] VertRefresh     56-75
EndSection
```
If that doesn't work, boot your ubuntu CD, mount your ubuntu partition(s) so you can edit etc/X11/xorg.conf again, and change it back

---

### Post by dcstar on 2008-01-05
> **geirha said:**
> What model is your monitor? My guess is that the HorizSync and VertRefresh options of your monitor section is not completely correct for your monitor. Commenting out those lines might work, as X then would try to detect those values itself (this has worked for most monitors I've encountered). 
```
Section "Monitor"
        Identifier      "SyncMaster"
        Option          "DPMS"
        [color=blue]#[/color] HorizSync       30-61
        [color=blue]#[/color] VertRefresh     56-75
EndSection
```
If that doesn't work, boot your ubuntu CD, mount your ubuntu partition(s) so you can edit etc/X11/xorg.conf again, and change it back

And you edit your file this way (in a terminal inside your logged in system):

```
gksudo gedit /etc/X11/xorg.conf
```

Once you have made the changes and saved the file, exit out of editor and press CTRL-ALT-Backspace to restart your X server with the new settings, you will soon see if things have changed.

---

### Post by kellemes on 2008-01-05
And if that doesn't work try adding the virtual line.. that fixed it for me ones..

```

SubSection "Display"
        Viewport   0 0
        Depth     24
        Virtual   1680 1050
        Modes    "1680x1050"
EndSubSection
```

---

### Post by oliviacond on 2008-01-06
my model is 153v, but i tried to select the model at Screens and Graphics option, broke the x server.

anyway, comment out those two lines work:)

---

