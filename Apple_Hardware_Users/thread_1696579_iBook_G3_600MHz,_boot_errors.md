---
title: "iBook G3 600MHz, boot errors"
date: 2011-02-27
forum: Apple Hardware Users
---

### Post by ClosedDoors1559 on 2011-02-27
Okay, so I downloaded the Ubuntu 11.04 Live CD PPC version, burned on a mini DVD. When I boot it on my iBook when holding C, it shows the Boot: screen. When I press Enter, it says 'Please wait, loading kernel...', and then shows 'Read failed'. Sometimes it also says something with 'Unable to open file, invalid device'. Can someone please help me? Thanks!

---

### Post by snafu006 on 2011-02-27
Have you tryed the live cd where you don't install it and it brings you to a desktop screen. A guy i helped out had the same thing happen to him and the way we got it to install is by getting the computer to boot to the live cd then to a desktop and install it that way.

One more thing use ubuntu 10.04 dont try the new stuff yet. Download ubuntu 10.04Powerpc

---

### Post by ClosedDoors1559 on 2011-02-27
> **snafu006 said:**
> Have you tryed the live cd where you don't install it and it brings you to a desktop screen. A guy i helped out had the same thing happen to him and the way we got it to install is by getting the computer to boot to the live cd then to a desktop and install it that way.

One more thing use ubuntu 10.04 dont try the new stuff yet. Download ubuntu 10.04Powerpc

Yes, I downloaded the Desktop version which allows to be used as live CD (the live CD where you don't have to install, but boots to the desktop). But I'm current;y downloading 10.10, I'll try that one and if it doesn't work, then I'll try 10.04. Thanks for the help so far :D!

---

### Post by snafu006 on 2011-02-27
ok but you might run in to the same problem if the happend just post back here but if you are able to get it to boot to a desktop you can install it from there.

---

### Post by snafu006 on 2011-02-27
[http://ubuntuforums.org/archive/index.php/t-694974.html](http://ubuntuforums.org/archive/index.php/t-694974.html)
live-nosplash-powerpc video=ofonly
i dont remener the powerpc part but the command you want is there when you press tab

This will get you to the desktop just press tab on yaboot enter the above line and that should work.

Oh and look at this post [http://art.ubuntuforums.org/showthread.php?t=1498559](http://art.ubuntuforums.org/showthread.php?t=1498559)

---

### Post by ClosedDoors1559 on 2011-02-27
Okay, I managed to boot in 10.10. It works, but that's all it does. As soon as I boot into the desktop, I see a line where the resolution 'ends', and underneath that line the beginning of the screen is shown. So, it has a resolution problem. The second problem I have is that Wi-fi works (lists the Wifi-spots), but if I enter my pass, it says Wi-fi has been disconnected. 3rd problem is that it has weird brightness control. But that isn't that important.

---

### Post by snafu006 on 2011-02-27
ok so are you able to get to the desktop? where you see the app bar at the top.

Its going to have a low resolution till we fix it and wifi we can fix to.

First step did you install ubuntu?

Second step fixing the low resolution.

And last wifi.

---

### Post by snafu006 on 2011-02-27
to fix the low resolution go to applications and find terminal.

in teriminal type sudo nano /etc/X11/xrog.conf press enter and type your password.

this should be blank maybe if so you need to enter this in if you ibook can connect to the net with an ethernet cord just copy and pasted. then press CTRL o press enter then CRTL x close terminal reboot computer.

Section "Files"
FontPath	"/usr/share/X11/fonts/misc"
FontPath	"/usr/share/X11/fonts/cyrillic"
FontPath	"/usr/share/X11/fonts/100dpi/:unscaled"
FontPath	"/usr/share/X11/fonts/75dpi/:unscaled"
FontPath	"/usr/share/X11/fonts/Type1"
FontPath	"/usr/share/X11/fonts/100dpi"
FontPath	"/usr/share/X11/fonts/75dpi"
# path to defoma fonts
FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
Load	"i2c"
Load	"bitmap"
Load	"ddc"
Load	"dri"
Load	"extmod"
Load	"freetype"
Load	"glx"
Load	"int10"
Load	"type1"
Load	"vbe"
EndSection

Section "InputDevice"
Identifier	"Generic Keyboard"
Driver	 "kbd"
Option	 "CoreKeyboard"
Option	 "XkbRules"	"xorg"
Option	 "XkbModel"	"pc104"
Option	 "XkbLayout"	"us"
EndSection

Section "InputDevice"
Identifier	"Configured Mouse"
Driver	 "mouse"
Option	 "CorePointer"
Option	 "Device"	 "/dev/input/mice"
Option	 "Protocol"	 "ExplorerPS/2"
Option	 "ZAxisMapping"	 "4 5"
Option	 "Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
Identifier	"Synaptics Touchpad"
Driver	 "synaptics"
Option	 "SendCoreEvents"	"true"
Option	 "Device"	 "/dev/psaux"
Option	 "Protocol"	 "auto-dev"
Option	 "HorizScrollDelta"	"0"
EndSection

Section "InputDevice"
Driver "wacom"
Identifier "stylus"
Option "Device" "/dev/wacom" # Change to 
# /dev/input/event
# for USB
Option "Type" "stylus"
Option "ForceDevice" "ISDV4" # Tablet PC ONLY
EndSection

Section "InputDevice"
Driver "wacom"
Identifier "eraser"
Option "Device" "/dev/wacom" # Change to 
# /dev/input/event
# for USB
Option "Type" "eraser"
Option "ForceDevice" "ISDV4" # Tablet PC ONLY
EndSection

Section "InputDevice"
Driver "wacom"
Identifier "cursor"
Option "Device" "/dev/wacom" # Change to 
# /dev/input/event
# for USB
Option "Type" "cursor"
Option "ForceDevice" "ISDV4" # Tablet PC ONLY
EndSection

Section "Device"
Identifier	"ATI Technologies, Inc. Radeon Mobility M6 LY [Radeon Mobility 9000]"
Driver	 "ati"
BusID	 "PCI:0:16:0"
Option	 "UseFBDev"	 "true"
EndSection

Section "Monitor"
Identifier	"Color LCD"
Option	 "DPMS"
EndSection

Section "Screen"
Identifier	"Default Screen"
Device	 "ATI Technologies, Inc. Radeon Mobility M6 LY [Radeon Mobility 9000]"
Monitor	 "Color LCD"
DefaultDepth	24
SubSection "Display"
Depth	 1
Modes	 "1024x768"
EndSubSection
SubSection "Display"
Depth	 4
Modes	 "1024x768"
EndSubSection
SubSection "Display"
Depth	 8
Modes	 "1024x768"
EndSubSection
SubSection "Display"
Depth	 15
Modes	 "1024x768"
EndSubSection
SubSection "Display"
Depth	 16
Modes	 "1024x768"
EndSubSection
SubSection "Display"
Depth	 24
Modes	 "1024x768"
EndSubSection
EndSection

Section "ServerLayout"
Identifier	"Default Layout"
Screen	 "Default Screen"
InputDevice	"Generic Keyboard"
InputDevice	"Configured Mouse"
InputDevice "stylus" "SendCoreEvents"
InputDevice "cursor" "SendCoreEvents"
InputDevice "eraser" "SendCoreEvents"
InputDevice	"Synaptics Touchpad"
EndSection

Section "DRI"
Mode	0666
EndSection

---

