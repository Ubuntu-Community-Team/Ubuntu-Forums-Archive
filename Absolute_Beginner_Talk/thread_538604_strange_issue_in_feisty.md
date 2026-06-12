---
title: "strange issue in feisty"
date: 2007-08-30
forum: Absolute Beginner Talk
---

### Post by sauravbhaumik on 2007-08-30
I've installed feisty; but whenever I type in the keyboard, the mouse seems to be reluctant to move. 
After it had been noticed, I tried a test:
without any writing environment I pressed the space key constantly and tried to move the mouse - I observed that the cursor was NOT moving as long I kept the key pressed.

Please help.
Saurav

---

### Post by quinnten83 on 2007-08-30
Hi, 
your post is extremely unclear to me.
Do you mean that while you are typing the mouse does not want to move, or do you mean that the mouse will stop reacting once you've typed something?
Also, If you want to get some help, you are going to have to provide specs, like what kind of mouse are you using? Usb/ PS2, which brand and which type, if you couls provide the same for the keyboard that will make sure more people in the know will react to your post.

---

### Post by sauravbhaumik on 2007-08-30
> **quinnten83 said:**
> Hi, 
your post is extremely unclear to me.
Do you mean that while you are typing the mouse does not want to move, or do you mean that the mouse will stop reacting once you've typed something?
Yes, the first is the case. Actually, as long as you keep a key pressed, the cursor doesn't move.
Edit: except SHIFT, CAPS, tab etc.


> Also, If you want to get some help, you are going to have to provide specs, like what kind of mouse are you using? Usb/ PS2, which brand and which type, if you couls provide the same for the keyboard that will make sure more people in the know will react to your post.

mouse - optical, PS-2 (company tech com)
keyboard - what can I say about keyboard except specifying the company name (TVS Gold)?

---

### Post by Uriel2006 on 2007-08-30
> **sauravbhaumik said:**
> Yes, the first is the case. Actually, as long as you keep a key pressed, the cursor doesn't move.
Edit: except SHIFT, CAPS, tab etc.




mouse - optical, PS-2 (company tech com)
keyboard - what can I say about keyboard except specifying the company name (TVS Gold)?

Hi, some BIOSes have the setting "USB KEYBOARD DOS mode", or something similar. May you check if you're using something like this? This gave similar problems to me, in the past.

hope being useful,

Uriel

---

### Post by sauravbhaumik on 2007-08-30
isn't there anyone to help me, or else, is the feisty version the  culprit?

---

### Post by sauravbhaumik on 2007-08-31
> **Uriel2006 said:**
> Hi, some BIOSes have the setting "USB KEYBOARD DOS mode", or something similar. May you check if you're using something like this? This gave similar problems to me, in the past.

hope being useful,

Uriel
It shouldn't be the case, because in edgy I never experienced the problem.

---

### Post by shinepuppy on 2007-09-27
I'm experiencing the same issue with Gutsy on my macbook pro. I noticed it when I used 'alt-tab' to change between windows or when I hit the tab key to jump to the next HTML object within a web page. I can also confirm the problem while holding the space bar down from within this reply text box. The mouse just doesn't want to move while a key on the keyboard is depressed and it happens within KDE, Gnome, and KDM :( Oh, and it only affects my external USB mouse (not the touchpad.)

Here are some of my specs:

```
jemanuel@jemanuel-laptop:~$ uname -a
Linux jemanuel-laptop 2.6.22-12-generic #1 SMP Sun Sep 23 18:11:30 GMT 2007 i686 GNU/Linux

jemanuel@jemanuel-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express PCI Express Root Port (rev 03)
00:07.0 Performance counters: Intel Corporation Unknown device 27a3 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
01:00.0 VGA compatible controller: ATI Technologies Inc M56P [Radeon Mobility X1600]
02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8053 PCI-E Gigabit Ethernet Controller (rev 22)
03:00.0 Network controller: Atheros Communications, Inc. AR5418 802.11a/b/g/n Wireless PCI Express Adapter (rev 01)
0c:03.0 FireWire (IEEE 1394): Texas Instruments TSB82AA2 IEEE-1394b Link Layer Controller (rev 01)

jemanuel@jemanuel-laptop:~$ lsusb
Bus 005 Device 003: ID 05ac:8300 Apple Computer, Inc.
Bus 005 Device 001: ID 0000:0000
Bus 004 Device 003: ID 05ac:8205 Apple Computer, Inc.
Bus 004 Device 001: ID 0000:0000
Bus 003 Device 002: ID 05ac:8240 Apple Computer, Inc.
Bus 003 Device 001: ID 0000:0000
Bus 001 Device 004: ID 05ac:021a Apple Computer, Inc.
Bus 001 Device 001: ID 0000:0000
Bus 002 Device 002: ID 045e:0053 Microsoft Corp.
Bus 002 Device 001: ID 0000:0000

jemanuel@jemanuel-laptop:~$ cat /etc/X11/xorg.conf
# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf(5) manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "ServerLayout"
        Identifier      "Default Layout"
  screen 0 "aticonfig-Screen[0]" 0 0
        Inputdevice     "Generic Keyboard"
        Inputdevice     "Configured Mouse"
        Inputdevice     "stylus"        "SendCoreEvents"
        Inputdevice     "cursor"        "SendCoreEvents"
        Inputdevice     "eraser"        "SendCoreEvents"
        Inputdevice     "Synaptics Touchpad"
EndSection

Section "Files"

        # path to defoma fonts
        Fontpath        "/usr/share/fonts/X11/misc"
        Fontpath        "/usr/share/fonts/X11/cyrillic"
        Fontpath        "/usr/share/fonts/X11/100dpi/:unscaled"
        Fontpath        "/usr/share/fonts/X11/75dpi/:unscaled"
        Fontpath        "/usr/share/fonts/X11/Type1"
        Fontpath        "/usr/share/fonts/X11/100dpi"
        Fontpath        "/usr/share/fonts/X11/75dpi"
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
        Option          "Device"        "/dev/input/mice"
        Option          "Protocol"      "ImPS/2"
        Option          "ZAxisMapping"  "4 5"
        Option          "Emulate3Buttons"       "true"
EndSection

Section "InputDevice"
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        Option          "SendCoreEvents"        "true"
        Option          "Device"        "/dev/psaux"
        Option          "Protocol"      "auto-dev"
        Option          "HorizScrollDelta"      "0"
        Option          "SHMConfig"     "on"
        #Option         "TwoFingerScroll"       "1"
        Option          "VertTwoFingerScroll" "1"
        Option          "HorizTwoFingerScroll" "1"
        Option          "MinSpeed" "1.10"
        Option          "MaxSpeed" "1.50"
        Option          "AccelFactor" "0.08"
EndSection

#       Section "InputDevice"
#       Identifier "Synaptics Touchpad"
#       Driver "synaptics"
#       Option "SendCoreEvents" "true"
#       Option "Device" "/dev/psaux"
#       Option "Protocol" "auto-dev"
#       Option "LeftEdge" "150"
#       Option "RightEdge" "1070"
#       Option "TopEdge" "100"
#       Option "BottomEdge" "310"
#       Option "FingerLow" "25"
#       Option "FingerHigh" "30"
#       Option "MaxTapTime" "180"
#       Option "MaxTapMove" "220"
#       Option "MaxDoubleTapTime" "180"
#       Option "HorizEdgeScroll" "0"
#       Option "VertEdgeScroll" "0"
#       Option "TapButton1" "0"
#       Option "TapButton2" "0"
#       Option "TapButton3" "0"
#       Option "LockedDrags" "off"
#       Option "VertScrollDelta" "20"
#       Option "HorizScrollDelta" "50"
#       Option "VertTwoFingerScroll" "1"
#       Option "HorizTwoFingerScroll" "1"
#       Option "MinSpeed" "1.10"
#       Option "MaxSpeed" "1.30"
#       Option "AccelFactor" "0.08"
#       Option "Emulate3Buttons" "true"
#       Option "SHMConfig" "on"
#       # corner buttons
#       Option "RTCornerButton" "0"
#       Option "RBCornerButton" "2"
#       Option "LTCornerButton" "0"
#       Option "LBCornerButton" "3"
#       EndSection

Section "InputDevice"
        Identifier      "stylus"
        Driver          "wacom"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"  "stylus"
        Option          "ForceDevice"   "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
        Identifier      "eraser"
        Driver          "wacom"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"  "eraser"
        Option          "ForceDevice"   "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
        Identifier      "cursor"
        Driver          "wacom"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"  "cursor"
        Option          "ForceDevice"   "ISDV4"# Tablet PC ONLY
EndSection

Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
EndSection

Section "Monitor"
        Identifier      "aticonfig-Monitor[0]"
        Option          "VendorName"    "ATI Proprietary Driver"
        Option          "ModelName"     "Generic Autodetecting Monitor"
        Option          "DPMS"  "true"
EndSection

Section "Device"
        Identifier      "Generic Video Card"
        Driver          "fglrx"
        Busid           "PCI:1:0:0"
EndSection

Section "Device"
        Identifier      "aticonfig-Device[0]"
        Driver          "fglrx"
        Option          "VideoOverlay"  "on"
        Option          "OpenGLOverlay" "off"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "Generic Video Card"
        Monitor         "Generic Monitor"
        Defaultdepth    24
        SubSection "Display"
                Depth   1
                Modes           "1024x768"      "800x600"       "640x480"
        EndSubSection
        SubSection "Display"
                Depth   4
                Modes           "1024x768"      "800x600"       "640x480"
        EndSubSection
        SubSection "Display"
                Depth   8
                Modes           "1024x768"      "800x600"       "640x480"
        EndSubSection
        SubSection "Display"
                Depth   15
                Modes           "1024x768"      "800x600"       "640x480"
        EndSubSection
        SubSection "Display"
                Depth   16
                Modes           "1024x768"      "800x600"       "640x480"
        EndSubSection
        SubSection "Display"
                Depth   24
                Modes           "1024x768"      "800x600"       "640x480"
        EndSubSection
EndSection

Section "Screen"
        Identifier      "aticonfig-Screen[0]"
        Device          "aticonfig-Device[0]"
        Monitor         "aticonfig-Monitor[0]"
        Defaultdepth    24
        SubSection "Display"
                Viewport        0       0
                Depth   24
        EndSubSection
EndSection

Section "DRI"
        Mode    0666
EndSection

Section "Extensions"
        Option          "Composite"     "0"
EndSection

```

I'm guessing it has something to do with the USB configuration

---

### Post by sauravbhaumik on 2007-09-27
> **shinepuppy said:**
> I'm experiencing the same issue with Gutsy on my macbook pro. I noticed it when I used 'alt-tab' to change between windows or when I hit the tab key to jump to the next HTML object within a web page. I can also confirm the problem while holding the space bar down from within this reply text box. The mouse just doesn't want to move while a key on the keyboard is depressed and it happens within KDE, Gnome, and KDM :( Oh, and it only affects my external USB mouse (not the touchpad.)

Here are some of my specs:

I'm guessing it has something to do with the USB configuration

But my mouse is not usb mouse, but ps2.
I do not experience this problem with Edgy 6.10.

---

### Post by shinepuppy on 2007-09-27
Try this:
[http://ubuntuforums.org/showthread.php?p=3435363](http://ubuntuforums.org/showthread.php?p=3435363)

It worked for me :)

---

### Post by sauravbhaumik on 2007-09-28
> **shinepuppy said:**
> Try this:
[http://ubuntuforums.org/showthread.php?p=3435363](http://ubuntuforums.org/showthread.php?p=3435363)

It worked for me :)

Thanks; I did it and the mouse seems to work fine :) :)
(Don't know if it would create problems later.)

---

