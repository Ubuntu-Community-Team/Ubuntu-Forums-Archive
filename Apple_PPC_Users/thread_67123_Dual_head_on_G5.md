---
title: "Dual head on G5"
date: 2005-09-19
forum: Apple PPC Users
---

### Post by heisters on 2005-09-19
Hi,

I'm trying to install Ubuntu (Breezy, sorry, but it's xorg stuff, so there shouldn't be a big difference between Hoary and Breezy, right?) on a PPC 64 (G5). It's worked very well, but I'd like to use both my monitors. The video card is an NVIDIA 5200 FX Ultra. Since this is PPC, there's no nVidia driver, just the OSS nv driver, so I can't use TwinView. Here's my xorg.conf with a little discussion below

```

Section "Files"
        FontPath        "/usr/share/X11/fonts/misc"
        FontPath        "/usr/share/X11/fonts/cyrillic"
        FontPath        "/usr/share/X11/fonts/100dpi/:unscaled"
        FontPath        "/usr/share/X11/fonts/75dpi/:unscaled"
        FontPath        "/usr/share/X11/fonts/Type1"
        FontPath        "/usr/share/X11/fonts/CID"
        FontPath        "/usr/share/X11/fonts/100dpi"
        FontPath        "/usr/share/X11/fonts/75dpi"
        # paths to defoma fonts
        FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
        FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
EndSection

Section "Module"
        Load    "GLcore"
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
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc104"
        Option          "XkbLayout"     "us"
EndSection

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ImPS/2"
        Option          "Emulate3Buttons"       "true"
        Option          "ZAxisMapping"          "4 5"
EndSection

Section "Device"
        Identifier      "GeForce FX 5200 Ultra"
        Driver          "nv"
        BusID           "PCI:240:16:0"
        Screen          0
EndSection

Section "Device"
        Identifier      "Geforce FX 5200 Ultra"
        Driver          "nv"
        BusID           "PCI:240:16:0"
        Screen          1
EndSection

Section "Monitor"
        Identifier      "DELL 1702FP"
        Option          "DPMS"
EndSection

Section "Monitor"
        Identifier      "DELL P1110"
        Option          "DPMS"
EndSection

Section "Screen"
        Identifier      "Primary Display"
        Device          "GeForce FX 5200 Ultra"
        Monitor         "DELL 1702FP"
        DefaultDepth    24
        SubSection "Display"
                Depth           24
                Modes           "1280x1024" "1024x768"
        EndSubSection
EndSection

Section "Screen"
        Identifier      "Secondary Display"
        Device          "GeForce FX 5200 Ultra"
        Monitor         "DELL P1110"
        DefaultDepth    24
        Subsection "Display"
                Depth           24
                Modes           "1280x1024" "1024x768"
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "Primary Layout"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
        Screen          "Primary Display"
        Screen          "Secondary Display" RightOf "Primary Display"
        Option          "Xinerama"      "on"
EndSection

Section "DRI"
        Mode    0666
EndSection

```

This conf leaves the second screen white. Xorg.0.log shows an apparently succesful setup:
```

(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Primary Layout"
(**) |-->Screen "Primary Display" (0)
(**) |   |-->Monitor "DELL 1702FP"
(**) |   |-->Device "GeForce FX 5200 Ultra"
(**) |-->Screen "Secondary Display" (1)
(**) |   |-->Monitor "DELL P1110"
(**) |   |-->Device "GeForce FX 5200 Ultra"
(**) |-->Input Device "Generic Keyboard"
(**) |-->Input Device "Configured Mouse"

```

i tried changing the second device section's identifier, so that each screen section can refer to a different identifier, but that throws the error that the device is already referred to by another device section (which makes sense), and xserver crashes.

So i thought maybe the second head needs to refer to a different PCI BusID, but lspci doesn't show another BusID for the video card. BTW, the BusID I'm using is obtained from the dpkg-reconfigure automagic.

Any thoughts? 

Thanks much.

---

### Post by heisters on 2005-09-20
anyone?

---

### Post by evilninja on 2008-03-10
Hi,

no solution but a question: did you manage to solve this issue? I got a 12" G4 PB here and it too has an Nvidia VGA chip (nVidia Corporation NV34M [GeForce FX Go5200]). Though X11/Xorg has changed a lot since 2005, I fail to get dual head working. Dual head was working fine with Gutsy on a 12" iBook (ATI Radeon VGA)

C.

---

### Post by stream303 on 2008-03-10
I've never set up a dual-head display with an nv card, but does anything in the nv manual (man nv) help:

```
Option "CrtcNumber" "integer"
              Many graphics cards with NVIDIA chips have  two  video  outputs.
              The  driver attempts to autodetect which one the monitor is con&#8208;
              nected to.  In the case that autodetection picks the wrong  one,
              this  option  may be used to force usage of a particular output.
              The options are "0" or "1".  Default: autodetected.

       Option "Dualhead" "boolean"
              Enables simple VBE-based dual head mode.   This  sets  the  same
              resolution  on both outputs and lays them out side-by-side.  The
              screens will be panned together as one big metamode if the  vir&#8208;
              tual desktop is larger than both screens combined.

       Option "FlatPanel" "boolean"
              The driver usually can autodetect the presence of a digital flat
              panel.  In the case that this fails, this option can be used  to
              force  the driver to treat the attached device as a digital flat
              panel.  With this driver, a digital flat panel will work only if
              it  was  POSTed  by  the  BIOS,  that is, the computer must have
              booted to the panel.  If you have a dual head card you may  also
              need  to  set  the  option CrtcNumber described above.  Default:
              autodetected.
```

I'm not trying to be a smart-a**, just wondering if this will lead in the right direction to be added to xorg.conf

I've never done it, but would love to see it work!

---

