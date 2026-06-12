---
title: "Resolution Problem-emergency!"
date: 2007-07-19
forum: Absolute Beginner Talk
---

### Post by ukulele_ninja on 2007-07-19
I tried lowering my resolution settings in the system>monitors section and it made everything really big and goofy...now i want my old settings back, but when i try to go in and change it, it looks all jarbled and crazy. after i restart it goes back to the lower res. what do i do??

Now when I restart it restarts and looks awful, all jarbled and a mess. What do i do?

---

### Post by asmoore82 on 2007-07-19
ctrl+atl+f1

login and ...
```

~$ sudo dpkg-reconfigure xserver-xorg
```

---

### Post by Snitz on 2007-07-19
If your motherboard is intel, this should help you.
[http://ubuntuguide.org/wiki/Ubuntu_Feisty#How_to_Correct_the_Graphics_Resolution_.28Intel.29](http://ubuntuguide.org/wiki/Ubuntu_Feisty#How_to_Correct_the_Graphics_Resolution_.28Intel.29)

---

### Post by forestpixie on 2007-07-19
did you make a backup of your old xorg.conf?

If so you might reboot into recovery, reboot and copy the backup over

Edit - or you could reconfigure :D - slow fingers and head

---

### Post by ukulele_ninja on 2007-07-19
I have an ATI Graphix card but I dont know about the motherboard, its a compaq computer. I finally got into the monitor settings again and lowered it back to 640X480 but it looks really big and awful...I just want my original settings back :(

---

### Post by ukulele_ninja on 2007-07-19
> **forestpixie said:**
> did you make a backup of your old xorg.conf?

If so you might reboot into recovery, reboot and copy the backup over

Edit - or you could reconfigure :D - slow fingers and head

what is xorg.config?

---

### Post by swoll1980 on 2007-07-19
It is the configuration file for the gui

---

### Post by forestpixie on 2007-07-19
how did you change the monitor settings? xorg.conf is the x server config file (I think)

---

### Post by ukulele_ninja on 2007-07-19
> **asmoore82 said:**
> ctrl+atl+f1

login and ...
```

~$ sudo dpkg-reconfigure xserver-xorg
```

How do I login on that screen??

---

### Post by Snitz on 2007-07-19
First, find out what's your video card type.

> lspci |grep VGA

And then, you see which driver is your computer using.

> gksudo gedit /etc/X11/xorg.conf

---

### Post by ukulele_ninja on 2007-07-19
> **forestpixie said:**
> how did you change the monitor settings? xorg.conf is the x server config file (I think)

I went to the K menu then system settings>monitor and changed it that way.

---

### Post by forestpixie on 2007-07-19
> **Snitz said:**
> First, find out what's your video card type.
And then, you see which driver is your computer using.

 do this - it's going were I was going :)

---

### Post by ukulele_ninja on 2007-07-19
> **Snitz said:**
> First, find out what's your video card type.



And then, you see which driver is your computer using.

...This makes me totally lame, but how do I make the vertical line in the console?

---

### Post by forestpixie on 2007-07-19
usually shift \

---

### Post by ukulele_ninja on 2007-07-19
Its a Radeon Xpress 200M

---

### Post by ukulele_ninja on 2007-07-19
> **forestpixie said:**
> do this - it's going were I was going :)

Its a Radeon Xpress 200M

---

### Post by misfitpierce on 2007-07-19
Make sure you have installed ATI fglrx restricted drivers under System - Admin - Restricted Devices/Drivers

---

### Post by ukulele_ninja on 2007-07-19
> **misfitpierce said:**
> Make sure you have installed ATI fglrx restricted drivers under System - Admin - Restricted Devices/Drivers

I looked it says:
Drivers Card- ATI fglrx
Driver- ATI

does that help?

---

### Post by forestpixie on 2007-07-19
in terminal

```
dir /etc/X11/xorg*
```

and post it here

in terminal 

```
gedit /etc/X11/xorg.conf
```

and post the file contents here

---

### Post by ukulele_ninja on 2007-07-19
> **forestpixie said:**
> in terminal

```
dir /etc/X11/xorg*
```

and post it here

in terminal 

```
gedit /etc/X11/xorg.conf
```

and post the file contents here

To the first one

it says /etc/X11/xorg.conf
it says /etc/X11/xorg.conf.3
it says /etc/X11/xorg.conf.7
it says /etc/X11/xorg.conf.1
it says /etc/X11/xorg.conf.4
it says /etc/X11/xorg.conf.8
it says /etc/X11/xorg.conf.10
it says /etc/X11/xorg.conf.5
it says /etc/X11/xorg.conf.9
it says /etc/X11/xorg.conf.2

The other one resulted with 'bad device'

---

### Post by forestpixie on 2007-07-19
are you running ubuntu or something else - if so replace gedit with your text editor.

---

### Post by forestpixie on 2007-07-19
if it's kubuntu I believe it'll be kate

---

### Post by alienexplorers on 2007-07-19
Please print out your xorg.conf by entering into the TERMINAL:
> cat /etc/X11/xorg.conf

---

### Post by ukulele_ninja on 2007-07-19
> **alienexplorers said:**
> Please print out your xorg.conf by entering into the TERMINAL:


Result:
cat: /etc/X11/xorg.config: No such file or directory

---

### Post by ukulele_ninja on 2007-07-19
> **forestpixie said:**
> if it's kubuntu I believe it'll be kate

Its Kubuntu, what do I put in Kate?

---

### Post by ukulele_ninja on 2007-07-19
> **forestpixie said:**
> in terminal

```
dir /etc/X11/xorg*
```

and post it here

in terminal 

```
gedit /etc/X11/xorg.conf
```

and post the file contents here

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

Section "Files"
  FontPath "/usr/share/fonts/X11/misc"
  FontPath "/usr/share/fonts/X11/cyrillic"
  FontPath "/usr/share/fonts/X11/100dpi/:unscaled"
  FontPath "/usr/share/fonts/X11/75dpi/:unscaled"
  FontPath "/usr/share/fonts/X11/Type1"
  FontPath "/usr/share/fonts/X11/100dpi"
  FontPath "/usr/share/fonts/X11/75dpi"
  # path to defoma fonts
  FontPath "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
  Load "i2c"
  Load "bitmap"
  Load "ddc"
  Load "extmod"
  Load "freetype"
  Load "int10"
  Load "vbe"
  load "glx"
  load "GLcore"
  load "dri"
  load "v4l"
EndSection

Section "InputDevice"
  Identifier "Generic Keyboard"
  Driver "kbd"
  option "CoreKeyboard"
  option "XkbRules" "xorg"
  option "XkbModel" "pc105"
  option "XkbLayout" "us"
EndSection

Section "InputDevice"
  Identifier "Configured Mouse"
  Driver "mouse"
  option "CorePointer"
  option "Device" "/dev/input/mice"
  option "Protocol" "ImPS/2"
  option "ZAxisMapping" "4 5"
  option "Emulate3Buttons" "true"
EndSection

Section "InputDevice"
  Identifier "Synaptics Touchpad"
  Driver "synaptics"
  option "SendCoreEvents" "true"
  option "Device" "/dev/psaux"
  option "Protocol" "auto-dev"
  option "HorizScrollDelta" "0"
EndSection

Section "InputDevice"
  Driver "wacom"
  Identifier "stylus"
  option "Device" "/dev/input/wacom"
  option "Type" "stylus"
  option "ForceDevice" "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver "wacom"
  Identifier "eraser"
  option "Device" "/dev/input/wacom"
  option "Type" "eraser"
  option "ForceDevice" "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver "wacom"
  Identifier "cursor"
  option "Device" "/dev/input/wacom"
  option "Type" "cursor"
  option "ForceDevice" "ISDV4"# Tablet PC ONLY
EndSection

Section "Device"
  identifier "ATI Technologies Inc ATI Radeon XPRESS 200M 5955 (PCIE)"
  boardname "ATI Radeon (fglrx)"
  busid "PCI:1:5:0"
  driver "ati"
  screen 0
  vendorname "ATI"
  option "MergedFB" "off"
EndSection

Section "Monitor"
  identifier "Generic Monitor"
  vendorname "Plug 'n' Play"
  modelname "Plug 'n' Play"
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
  gamma 1.0
EndSection

Section "Screen"
  Identifier "Default Screen"
  Device "ATI Technologies Inc ATI Radeon XPRESS 200M 5955 (PCIE)"
  Monitor "Generic Monitor"
  DefaultDepth 24
  SubSection "Display"
    depth 24
    virtual 640 480
    modes "640x480@60"
  EndSubSection
EndSection

Section "ServerLayout"
  Identifier "Default Layout"
  screen 0 "Default Screen" 0 0
  InputDevice "Generic Keyboard"
  InputDevice "Configured Mouse"
  InputDevice "stylus" "SendCoreEvents"
  InputDevice "cursor" "SendCoreEvents"
  InputDevice "eraser" "SendCoreEvents"
  InputDevice "Synaptics Touchpad"
EndSection

Section "DRI"
  Mode 0666
EndSection
Section "device" #        
  identifier "device1"
  boardname "ATI Radeon (fglrx)"
  busid "PCI:1:5:0"
  driver "ati"
  screen 1
  vendorname "ATI"
  option "MergedFB" "off"
EndSection
Section "screen" #        
  identifier "screen1"
  device "device1"
  defaultdepth 24
  monitor "monitor1"
  SubSection "Display"
    depth 24
    modes "640x480@60"
  EndSubSection
EndSection
Section "monitor" #        
  identifier "monitor1"
  vendorname "Plug 'n' Play"
  modelname "Plug 'n' Play"
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
  gamma 1.0
EndSection
Section "ServerFlags"
EndSection

---

### Post by ukulele_ninja on 2007-07-19
Any help you guys can give me is much appreciated! I really want to get this taken care of ASAP!

---

### Post by forestpixie on 2007-07-20
I fyou still have a problem you can either replace xorg.conf with the latest xorg.<number> - you can find the time stamp information in your file manager

or reconfigurre your graphics card with

sudo dpkg-reconfigure -p high xserver-xorg

answer the questions, use default if your not sure and then

sudo reboot

---

