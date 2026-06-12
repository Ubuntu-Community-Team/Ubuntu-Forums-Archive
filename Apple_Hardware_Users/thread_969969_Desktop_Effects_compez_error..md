---
title: "Desktop Effects compez error."
date: 2008-11-03
forum: Apple Hardware Users
---

### Post by crapple on 2008-11-03
I was searching the web on why my desktop effects don't work. When I try to enable them i get a message saying Desktop Effects could not be enabled. I typed this into terminal and get this error

```
harel@biggie3linux:~$ SKIP_CHECKS=yes compiz
Checking for Xgl: not present. 
No whitelisted driver found
SKIP_CHECKS is yes, so continuing despite problems.
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1024x768) to maximum 3D texture size (2048): Passed.
Checking for nVidia: not present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
/usr/bin/compiz.real (core) - Fatal: No GLXFBConfig for default depth, this isn't going to work.
/usr/bin/compiz.real (core) - Error: Failed to manage screen: 0
/usr/bin/compiz.real (core) - Fatal: No manageable screens found on display :0.0

```

My xorg file looks like this. I can not remove the screen 0 because that is what causes my graphical interface to work. (Long story why I have this configuration. Basically original didn't work. I have an emac.)

```
# xorg.conf (X.Org X Window System server configuration file)
#
# See the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)

# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.

Section "ServerLayout"
        Identifier      "XFree86 Configured"
        Screen          0 "Screen0" 0 0
        InputDevice     "Mouse0" "CorePointer"
        InputDevice     "Keyboard0" "CoreKeyboard"
        Option          "OffTime" "10"
EndSection

Section "Files"
# RgbPath is the location of the RGB database.  Note, this is the name of the
# file minus the extension (like ".txt" or ".db").  There is normally
# no need to change the default.
# Multiple FontPath entries are allowed (they are concatenated together)

       RgbPath		"/usr/share/X11/rgb.txt"
      #FontPath		"/usr/share/X11/fonts/misc:unscaled"
      #FontPath		"/usr/share/X11/fonts/Type1/"
      #FontPath		"/usr/share/X11/fonts/Speedo/"
      #FontPath		"/usr/share/X11/fonts/75dpi:unscaled"
      #FontPath		"/usr/share/X11/fonts/100dpi:unscaled"
EndSection

Section "Module"
        Load            "dbe"
        Load            "extmod"
        Load            "fbdevhw"
        Load            "freetype"
        Load            "type1"
        #Load           "dri"
EndSection

Section "InputDevice"
        Identifier      "Keyboard0"
        Driver          "kbd"
# Change "XkbModel" to "macintosh_old" if you are using
# the deprecated adb keycodes.
        Option          "XkbModel"      "macintosh"
        Option          "XkbLayout"     "us"
        Option          "XkbOptions"    "grp:caps_toggle"
EndSection

Section "InputDevice"
        Identifier      "Mouse0"
        Driver          "mouse"
        Option          "ZAxisMapping"  "4 5"
        Option          "Protocol"      "IMPS/2"
        Option          "Device"        "/dev/input/mice"
EndSection

Section "Monitor"
        Identifier      "Monitor0"
        ModelName       "Monitor Model"
        Option          "DPMS"
        HorizSync       30-82
        VertRefresh     50-60
EndSection

Section "Device"
        Identifier      "Card0"
        #Option         "ShadowFB"      "true"
        #Option         "fbdev"         "/dev/fb0"
        Driver          "fbdev"
        #BusID          "PCI:0:16:0"
        Option          "UseFBDev"      "true"
EndSection

Section "Screen"
        Identifier      "Screen0"
        Device          "Card0"
        Monitor         "Monitor0"
        DefaultDepth    24
        SubSection "Display"
                Depth   24
                Modes   "1024x768"
        EndSubSection
        SubSection "Display"
                Depth   16
                Modes   "1024x768"
        EndSubSection
        SubSection "Display"
                Depth   15
                Modes   "1024x768"
        EndSubSection
        SubSection "Display"
                Depth   8
                Modes   "1024x768"
        EndSubSection
EndSection

Section "DRI"
        Group           0
        Mode            0666
EndSection
```

Is there anyway to fix this or get around it? Thanks

---

### Post by gatlin on 2008-11-24
I am having a similar problem as described above, including the "No display found" issue. I have a black MacBook circa 2006 (December), and when I first installed the Ubuntu-desktop package (from Xubuntu) I had compiz.  Now? Not so much.  It _might_ be something from when I did the "Pure Gnome" command that removes all traces of Xubuntu from the system, but since Xubuntu doesn't use compiz that is a bit suspect.  

I don't know what I need to give because this is my first foray into Linux on the Mac but any assistance would be appreciated.  Thanks!

---

