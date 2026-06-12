---
title: "Installing Ubuntu on a Toshiba Satellite 4030CDT"
date: 2006-08-31
forum: Absolute Beginner Talk
---

### Post by pasan on 2006-08-31
Following on from the title...I was thinking the latest version of Ubuntu probably be bit too heavy for an old Laptop like the Toshiba 4030CDT (which runs at 300MHz!). I was wondering if it's possible to get older distributions of Ubuntu that may be more suited for an old machine or if anyone could recommend a light weight Linux distro that might run smoothly on such a system? Thanks. :)

---

### Post by XaeroDegreaz on 2006-08-31
Fedora Core from Redhat :)

But really, Ubuntu is great, it isn;t intensive at all. Matter of fact, I haven;t met up with a Linux system yet that really is! Matter of fact like, if you can run Windows on your machine, then you can definately run Linux, it is even less intensive than that!

Good luck :)

[http://fedora.redhat.com/](http://fedora.redhat.com/) if you want to check it out.

---

### Post by benfindlay on 2006-08-31
The latest version of Xubuntu should run well on it. It uses a much lighter-weight graphics interface, but still looks very impressive!

---

### Post by pasan on 2006-08-31
Does Xubuntu come with software like Firefox, Openoffice, Gimp and Gaim? Those are the ones I really use.

---

### Post by amo-ej1 on 2006-08-31
Yes it does but be aware that openoffice has always been resource hungry and it will always be. It's always suggested to keep to the most recent version of software, so running an old linux distribution will get you an outdated/insecure setup which doesn't _have_ to be much faster. I installed the regular ubuntu on a P III 850 / 128 meg ram recently and increased the speed by removing most eyecandy and unneeded services. Not by installing the oldest linux distribution I could find ...

my 2 cents

---

### Post by 3rdalbum on 2006-08-31
Xubuntu doesn't come with OpenOffice.org, but it does include Abiword.

OpenOffice.org can be easily installed through the Synaptic Package Manager though.

If you're interested in lightweight-yet-fully-functional distros, try Zenwalk. It looks excellent.

---

### Post by euphro on 2006-11-03
I've got a Satellite 4030 CDT.  I started installing Dapper from the CD-ROM but gave up because it seemed to be taking forever and the mouse-cursor kept freezing-up.  I then tried Breezy, which installed like a dream, and after some googling I switched to Xubuntu, which has been great.  One tip, though, for the display choose 16 bits as your default depth, otherwise you won't be able to use the full area of your screen :)

---

### Post by fernando50 on 2007-03-24
I successfully installed Kubuntu 6.06.1 LTS alternate i386 onto my Toshiba Satellite 4030CDT. Now I'm going through the motion of making changes to the KDE Desktop settings to suit my preferences. I noticed that the "K Menu>System Settings>Display" selection does correctly identify the Trident Cyber 9525 video card, but only the "Generic" version and not the "DVD" version which is built with 2560KB of Video Ram. Unfortunately the settings don't allow the Video Ram amount to be changed from the frozen selection of 256KB. I even changed the Graphics Card device selection to "Toshiba Satellite 4030CDT", but it made no difference (even after rebooting) for I'm unable to change the video ram amount. Sorry in advance for the length of this posting, but I know that the config file will explain to the advance linux users what needs to be done to help me sort out the Graphics Card settings (even force a change). Thank you in advance for any assistance :) 

Here is the "/etc/X11/xorg.conf" file settings:
------------------------------------------------------
Section "Files"
  FontPath "/usr/share/X11/fonts/misc"
  FontPath "/usr/share/X11/fonts/cyrillic"
  FontPath "/usr/share/X11/fonts/100dpi/:unscaled"
  FontPath "/usr/share/X11/fonts/75dpi/:unscaled"
  FontPath "/usr/share/X11/fonts/Type1"
  FontPath "/usr/share/X11/fonts/100dpi"
  FontPath "/usr/share/X11/fonts/75dpi"
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
  Load "type1"
  Load "vbe"
  load "glx"
  load "GLcore"
  load "v4l"
EndSection

Section "InputDevice"
  Identifier "Generic Keyboard"
  Driver "kbd"
  option "CoreKeyboard"
  option "XkbRules" "xorg"
  option "XkbModel" "pc104"
  option "XkbLayout" "us"
EndSection

Section "InputDevice"
  Identifier "Configured Mouse"
  Driver "mouse"
  option "CorePointer"
  option "Device" "/dev/input/mice"
  option "Protocol" "ExplorerPS/2"
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
  option "Device" "/dev/wacom"# Change to 
  option "Type" "stylus"
  option "ForceDevice" "ISDV4"# Tablet PC ONLY
  # /dev/input/event
  # for USB
EndSection

Section "InputDevice"
  Driver "wacom"
  Identifier "eraser"
  option "Device" "/dev/wacom"# Change to 
  option "Type" "eraser"
  option "ForceDevice" "ISDV4"# Tablet PC ONLY
  # /dev/input/event
  # for USB
EndSection

Section "InputDevice"
  Driver "wacom"
  Identifier "cursor"
  option "Device" "/dev/wacom"# Change to 
  option "Type" "cursor"
  option "ForceDevice" "ISDV4"# Tablet PC ONLY
  # /dev/input/event
  # for USB
EndSection

Section "Device"
  identifier "Trident Microsystems Cyber 9525"
  boardname "Toshiba Satellite 4030CDT"
  busid "PCI:0:4:0"
  driver "trident"
  screen 0
  vendorname "Toshiba"
  option "cyber_shadow"
EndSection

Section "Monitor"
  identifier "Generic Monitor"
  vendorname "Generic"
  modelname "Flat Panel 1024x768"
  HorizSync 31.5-55
  VertRefresh 40-70
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
  modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -vsync -hsync
  modeline  "1152x768@54" 64.995 1152 1178 1314 1472 768 771 777 806 +hsync +vsync
  modeline  "1280x854" 80.0 1280 1309 1460 1636 854 857 864 896 +hsync +vsync
  gamma 1.0
EndSection

Section "Screen"
  Identifier "Default Screen"
  Device "Trident Microsystems Cyber 9525"
  Monitor "Generic Monitor"
  DefaultDepth 24
  SubSection "Display"
    depth 24
    modes "800x600@60" "1024x768@60" "800x600@56" "1152x768@54" "640x480@60" "1280x854"
  EndSubSection
EndSection

Section "ServerLayout"
  Identifier "Default Layout"
  screen 0 "Default Screen" 0 0
  screen 1 "screen1" 0 0
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
  boardname "Toshiba Satellite 4030CDT"
  busid "PCI:0:4:0"
  driver "trident"
  screen 1
  vendorname "Toshiba"
  option "cyber_shadow"
EndSection
Section "screen" #    
  identifier "screen1"
  device "device1"
  defaultdepth 24
  monitor "monitor1"
  SubSection "Display"
    depth 24
    modes "800x600@60" "1024x768@70" "800x600@56" "1024x768@60" "640x480@60" "1152x768@54" "1280x854" "1280x960@60" "1280x1024@60"
  EndSubSection
EndSection
Section "monitor" #    
  identifier "monitor1"
  vendorname "Generic"
  modelname "1280x1024 @ 60 Hz"
  HorizSync 31.5-64.3
  VertRefresh 50-70
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
  modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "1024x768@70" 75.0 1024 1048 1184 1328 768 771 777 806 -vsync -hsync
  modeline  "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -vsync -hsync
  modeline  "1152x768@54" 64.995 1152 1178 1314 1472 768 771 777 806 +hsync +vsync
  modeline  "1280x854" 80.0 1280 1309 1460 1636 854 857 864 896 +hsync +vsync
  modeline  "1280x960@60" 102.1 1280 1360 1496 1712 960 961 964 994 -hsync +vsync
  modeline  "1280x1024@60" 108.0 1280 1328 1440 1688 1024 1025 1028 1066 +hsync +vsync
  gamma 1.0
EndSection
Section "ServerFlags"
  option "Xinerama" "true"
EndSection

---

### Post by luzius on 2007-10-09
The Satellite 4030CDT runs with a 1024x768 16 bit display, but** I had to bring the memory to 192MB** with a 128MB chip.
I had my best results with  Xubuntu 7.04, after many unsuccessful tries with other small distros (video problems and lack of german language support).

---

### Post by Mac Tzu on 2008-03-14
Hey guys,

I have couple of issue with xubuntu on my 4030cdt.  1stly I should let you know that i have 128m of ram atm.  I have just installed gutsy on it no problem.  
I have a problem here it can't or won't shutdown properly.  I have shutdown from xserver and root term.  It goes though all the normal shutdown steps then brings up root terminal again. 

Any help would be awesome

Mac

---

### Post by gobuntu on 2008-03-14
> **pasan said:**
> Following on from the title...I was thinking the latest version of Ubuntu probably be bit too heavy for an old Laptop like the Toshiba 4030CDT (which runs at 300MHz!). I was wondering if it's possible to get older distributions of Ubuntu that may be more suited for an old machine or if anyone could recommend a light weight Linux distro that might run smoothly on such a system? Thanks. :)

Hi Pasan,

You can resolve easily!

Just boot the Live CD (tests and actually runs your system with a non-install) and you will find out!

I think even the latest Gutsy will run.

As you've been said, you wouldn't run Compiz graphics etc. but that's not what you are after anyway.

---

