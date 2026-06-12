---
title: "can't change screen resolution"
date: 2007-11-12
forum: Absolute Beginner Talk
---

### Post by BlastOButter42 on 2007-11-12
Sorry if this has been covered before but I didn't find a thread dealing specifically with this, or at least one that I could understand (I'm pretty new to Ubuntu so I'd appreciate it greatly if help could be given very step-by-step and un-technically).

My laptop has a widescreen display, and currently the screen resolution in Ubuntu is at 1024x768, which makes everything stretched out horizontally. I'd like to change the resolution to 1200x800, what I'm used to from Windows, or at least something with a 3:2 aspect ratio.

But when I go to System>Preferences>Screen Resolution, the only option under "Resolution" is 1024x768. Is there any way to add to or edit these options so I can set the resolution to 1200x800?

---

### Post by taurus on 2007-11-12
What video card do you have and have you installed a driver for it?

---

### Post by BlastOButter42 on 2007-11-12
It's a Mobile Intel 915GM/GMS, 910GML Express with 128MB of memory. I don't know about the driver...I haven't installed anything for it.
The laptop has a 1.5 GHz processor with 1 gig of RAM.

---

### Post by taurus on 2007-11-12
Look in /etc/X11/xorg.conf especially the "Section Device" to see what driver you are using.

```
cat /etc/X11/xorg.conf
```

---

### Post by BlastOButter42 on 2007-11-12
That says the driver is "i810":

Section "Device"
        Identifier      "Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller"
        Driver          "i810"
        BusID           "PCI:0:2:0"
EndSection

---

### Post by taurus on 2007-11-12
What are the resolutions you have in that file, further down?

Include the whole file if you wish.

---

### Post by BlastOButter42 on 2007-11-12
Here ya go:
The pertinent section would seem to be this:
Section "Screen"
        Identifier      "Default Screen"
        Device          "Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller"
        Monitor         "Generic Monitor"
        DefaultDepth    24
        SubSection "Display"
                Depth           1
                Modes           "1280x800"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1280x800"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1280x800"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1280x800"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1280x800"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1280x800"
        EndSubSection
EndSection



Here's the whole thing:

Section "Files"
        FontPath        "/usr/share/fonts/X11/misc"
        FontPath        "/usr/share/fonts/X11/cyrillic"
        FontPath        "/usr/share/fonts/X11/100dpi/:unscaled"
        FontPath        "/usr/share/fonts/X11/75dpi/:unscaled"
        FontPath        "/usr/share/fonts/X11/Type1"
        FontPath        "/usr/share/fonts/X11/100dpi"
        FontPath        "/usr/share/fonts/X11/75dpi"
        # path to defoma fonts
        FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
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
        Load    "vbe"
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
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        Option          "SendCoreEvents"        "true"
        Option          "Device"                "/dev/psaux"
        Option          "Protocol"              "auto-dev"
        Option          "HorizScrollDelta"      "0"
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
        Identifier      "Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller"
        Driver          "i810"
        BusID           "PCI:0:2:0"
EndSection

Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller"
        Monitor         "Generic Monitor"
        DefaultDepth    24
        SubSection "Display"
                Depth           1
                Modes           "1280x800"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1280x800"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1280x800"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1280x800"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1280x800"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1280x800"
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
        InputDevice     "stylus"        "SendCoreEvents"
        InputDevice     "cursor"        "SendCoreEvents"
        InputDevice     "eraser"        "SendCoreEvents"
        InputDevice     "Synaptics Touchpad"
EndSection

Section "DRI"
        Mode    0666
EndSection

---

### Post by taurus on 2007-11-12
Here's something for you to look at.

[http://ubuntuforums.org/showthread.php?t=609836&highlight=915resolution](http://ubuntuforums.org/showthread.php?t=609836&highlight=915resolution)

p.s.  915resolution should be in the repos so fire up synaptic and Search for it.

---

### Post by BlastOButter42 on 2007-11-12
I got the program, but could you help me use it? I'm really lost reading the instructions.

---

### Post by taurus on 2007-11-12
So you have installed 915resolution from the repos, right.  Have you tried any command from that link yet?

---

### Post by BlastOButter42 on 2007-11-12
I followed the links to this: [http://www.geocities.com/stomljen/readme.html](http://www.geocities.com/stomljen/readme.html), and I put in "915resolution [-l] [mode X Y] [bits/pixel]" but it just says "Unable to obtain the proper IO permissions: Operation not permitted".

---

### Post by taurus on 2007-11-12
Put the **sudo** in front of the command since you need to be root to write to system file.

---

### Post by BlastOButter42 on 2007-11-12
Ok, so when I put in "sudo 915resolution -l" it says this: 

Chipset: 915GM
BIOS: TYPE 1
Mode Table Offset: $C0000 + $269
Mode Table Entries: 36

Mode 30 : 640x480, 8 bits/pixel
Mode 32 : 800x600, 8 bits/pixel
Mode 34 : 1024x768, 8 bits/pixel
Mode 38 : 1280x1024, 8 bits/pixel
Mode 3a : 1600x1200, 8 bits/pixel
Mode 3c : 1280x800, 8 bits/pixel
Mode 41 : 640x480, 16 bits/pixel
Mode 43 : 800x600, 16 bits/pixel
Mode 45 : 1024x768, 16 bits/pixel
Mode 49 : 1280x1024, 16 bits/pixel
Mode 4b : 1600x1200, 16 bits/pixel
Mode 4d : 1280x800, 16 bits/pixel
Mode 50 : 640x480, 32 bits/pixel
Mode 52 : 800x600, 32 bits/pixel
Mode 54 : 1024x768, 32 bits/pixel
Mode 58 : 1280x1024, 32 bits/pixel
Mode 5a : 1600x1200, 32 bits/pixel
Mode 5c : 1280x800, 32 bits/pixel

The readme talks about replacing mode 38; should I do that? Mode 3c already has what I want.

---

### Post by taurus on 2007-11-12
Don't you mean you need to run something like

```
sudo 915resolution 3c 1280 800 **24**
```
since you want to use 24 bit/pixel.

---

### Post by BlastOButter42 on 2007-11-12
So then what should I do? The next thing seems to be in Step 7 but I don't run SUSE.

---

### Post by taurus on 2007-11-12
You still can put boot.local in /etc/init.d though!

```
sudo boot.local /etc/init.d/boot.local
sudo chmod 755 /etc/init.d/boot.local
```

boot.local:
```

#! /bin/bash
#
# Copyright (c) 2002 SuSE Linux AG Nuernberg, Germany.  All rights reserved.
#
# Author: Werner Fink , 1996
#         Burchard Steinbild, 1996
#
# /etc/init.d/boot.local
#
# script with local commands to be executed from init on system startup
#
# Here you should add things, that should happen directly after booting
# before we're going to the first run level.
#

/usr/bin/915resolution 3c 1280 800    

```

Then, reboot and see what happens.

p.s.  Did you install 915resolution in /usr/bin?

```
whereis 915resolution
```

---

### Post by BlastOButter42 on 2007-11-12
I don't already have a boot.local file in the init.d foler; I tried to create it but it says I don't have permissions to write to the init.d folder.

robert@MYRTLE-ubuntu:~$ whereis 915resolution
915resolution: /usr/sbin/915resolution /usr/share/man/man8/915resolution.8.gz

---

### Post by taurus on 2007-11-12
You need to create one as root.

```
gksudo gedit /etc/init.d/boot.local
```

And paste these in there.

```

#!/bin/bash
#
# Copyright (c) 2002 SuSE Linux AG Nuernberg, Germany.  All rights reserved.
#
# Author: Werner Fink , 1996
#         Burchard Steinbild, 1996
#
# /etc/init.d/boot.local
#
# script with local commands to be executed from init on system startup
#
# Here you should add things, that should happen directly after booting
# before we're going to the first run level.
#

/usr/sbin/915resolution 3c 1280 800

```
Save it and then change the permission to executable.

```
sudo chmod 755 /etc/init.d/boot.local
```
Now, reboot.

---

### Post by BlastOButter42 on 2007-11-12
Brilliant. Thanks ***so*** much for helping out a newbie. I must have been very frustrating, but just by doing this, I learned a lot.
This is one of the reasons Linux is so great -- its community is made up of people like you.

---

### Post by taurus on 2007-11-12
I'll take it everything is rosy your end, 1280x800, then.

---

### Post by BlastOButter42 on 2007-11-12
Yup. Thanks again.

---

### Post by taurus on 2007-11-12
You're welcome.

---

