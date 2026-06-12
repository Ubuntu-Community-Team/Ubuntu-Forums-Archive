---
title: "Laggy Screensavers"
date: 2006-08-14
forum: Absolute Beginner Talk
---

### Post by d4rk on 2006-08-14
When I had innstalled Ubuntu, I explored the system widley. I came over all the screensavers. Some of them was pretty nice, others may a bit cheap. But those whom was 3d, and goodlooking, was buggy/laggy, like I had a bad graphic card. I have 7900GT, so I don't think that's a problem.

But I know innstalling drivers to Linux is pretty hard, but i used EasyUbuntu, and that did the job. But now, about none of the screensavers work, and they who work, i still laggy/buggy.

Is there a possibility that EasyUbuntu didn't do its job ?

---

### Post by Perfect Storm on 2006-08-14
What does your Xorg.conf say?
```
cat /etc/X11/xorg.conf
```

Also check if nvidia-glx is installed.

---

### Post by d4rk on 2006-08-15
> **Artificial Intelligence said:**
> What does your Xorg.conf say?
```
cat /etc/X11/xorg.conf
```

Also check if nvidia-glx is installed.

SORRY !  I LOST MY INTERNET CONNECTION, SO I HAVE NOT HAD THE CHANCE TO ANSWER !

It says:
Section "Screen"
        Identifier      "Default Screen"
        Device          "NVIDIA Corporation NVIDIA Default Card"
        Monitor         "SyncMaster"
        DefaultDepth    24
        SubSection "Display"

nvidia-glx is innstalled.

---

### Post by syedn on 2006-08-15
Somewhere above that it should also list your graphics card as a device and under that a subsection should list the driver used with that device.. if it says nvidia then you have the right drivers.. if it says nv, you won't have 3d acceleration which would explain the laggy screensavers.  Same thing happened to me before I had the driver installed correctly.

---

### Post by d4rk on 2006-08-15
> **syedn said:**
> Somewhere above that it should also list your graphics card as a device and under that a subsection should list the driver used with that device.. if it says nvidia then you have the right drivers.. if it says nv, you won't have 3d acceleration which would explain the laggy screensavers.  Same thing happened to me before I had the driver installed correctly.


> Section "Files"
        FontPath        "/usr/share/X11/fonts/misc"
        FontPath        "/usr/share/X11/fonts/cyrillic"
        FontPath        "/usr/share/X11/fonts/100dpi/:unscaled"
        FontPath        "/usr/share/X11/fonts/75dpi/:unscaled"
        FontPath        "/usr/share/X11/fonts/Type1"
        FontPath        "/usr/share/X11/fonts/100dpi"
        FontPath        "/usr/share/X11/fonts/75dpi"
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
        Load    "type1"
        Load    "vbe"
EndSection

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "no"
EndSection

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ExplorerPS/2"
        Option          "ZAxisMapping"          "4 5"
        Option          "Emulate3Buttons"       "true"
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
        Identifier      "NVIDIA Corporation NVIDIA Default Card"
        Driver          "nv"
        BusID           "PCI:1:0:0"
EndSection

Section "Monitor"
        Identifier      "SyncMaster"
        Option          "DPMS"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "NVIDIA Corporation NVIDIA Default Card"
        Monitor         "SyncMaster"
        DefaultDepth    24
        SubSection "Display"
                Depth           1
                Modes           "1280x1024" "1152x864" "1024x768" "832x624" "800 x600" "720x400" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1280x1024" "1152x864" "1024x768" "832x624" "800 x600" "720x400" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1280x1024" "1152x864" "1024x768" "832x624" "800 x600" "720x400" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1280x1024" "1152x864" "1024x768" "832x624" "800 x600" "720x400" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1280x1024" "1152x864" "1024x768" "832x624" "800 x600" "720x400" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1280x1024" "1152x864" "1024x768" "832x624" "800 x600" "720x400" "640x480"
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
        InputDevice     "stylus" "SendCoreEvents"
        InputDevice     "cursor" "SendCoreEvents"
        InputDevice     "eraser" "SendCoreEvents"
EndSection

Section "DRI"
        Mode    0666
EndSection

This is what I get.

---

### Post by Chemroydal Tissue on 2006-08-15
In this section (the 8th "Section" down in your xorg.conf):
```
Section "Device"
Identifier "NVIDIA Corporation NVIDIA Default Card"
Driver "nv"
BusID "PCI:1:0:0"
EndSection
```

You need to tell X to use the correct driver. Open a terminal and type:

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup
```

(always make backups!) then:

```
sudo gedit /etc/X11/xorg.conf
```

at this point, change "nv" to "nvidia"

followed by:

```
sudo reboot
```

When your machine restarts, you should be using the correct drivers. IF SOMETHING GOES WRONG, from the command line type:

```
cp /etc/X11/xorg.conf_backup /etc/X11/xorg.conf
```

followed by:

```
sudo reboot
```

Then go [here](http://www.ubuntuforums.org/showthread.php?t=139264) and try to find the solution.

---

### Post by TooDamFast on 2006-08-15
could be a run-a-way system process.  how is your cpu usage? This happens to me when Perl goes wonky and uses 99% of my cpu.

---

### Post by d4rk on 2006-08-16
Chemroydal Tissue: I'm sorry for such a late answer, but thanks alot man !
It realy did the thing, no laggy screensavers, and all of em work, and nvidia is again, spamming my boot ;)

---

### Post by Chemroydal Tissue on 2006-08-19
> **d4rk said:**
> Chemroydal Tissue: I'm sorry for such a late answer, but thanks alot man !
It realy did the thing, no laggy screensavers, and all of em work, and nvidia is again, spamming my boot ;)

Re: the splashscreen: Just add 
```
Option "NoLogo"
```
 at the end of the same Section. :mrgreen:

EDIT: It should look similar to this:

```
Section "Device"
	Identifier	"NVIDIA Corporation NV43 [GeForce 6600]"
	Driver		"nvidia"
	BusID		"PCI:1:0:0"
	Option		"NoLogo"
EndSection
```

---

