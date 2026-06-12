---
title: "Screen Resolution 1280 x 1024"
date: 2008-03-15
forum: Absolute Beginner Talk
---

### Post by rwakefie on 2008-03-15
I originally installed Ubuntu 7.10 on a 15 in monitor and now I am switching to a 20 inch monitor and I cannot get Ubuntu to display the proper resolution.

I have an Nvidia Gforce 5700, and I install the drivers for this through Envy. The proper driver appears to be installed.

When I try to set the proper screen resolution through System > Preferences > Screen Resolution or through the Nvidia settings it does not seem to go higher than 1024x768.

I have also tried to reconfigure the Xserver myself by running sudo dpkg-reconfigure xserver-xorg and selecting the proper screen resolution and this also did not work.

If I hook this up from my 15in monitor to my 20in monitor it will work with the resolution of 1024x768. If I restart it will not display and tell me video mode not supported.

Here is what my xorg.conf looks like.

Section "Files"
EndSection

Section "InputDevice"
 Identifier "Generic Keyboard"
 Driver "kbd"
 Option "CoreKeyboard"
 Option "XkbRules" "xorg"
 Option "XkbModel" "pc105"
 Option "XkbLayout" "us"
 Option "XkbVariant" "us"
EndSection

Section "InputDevice"
 Identifier "Configured Mouse"
 Driver "mouse"
 Option "CorePointer"
 Option "Device" "/dev/input/mice"
 Option "Protocol" "ExplorerPS/2"
 Option "ZAxisMapping" "4 5"
 Option "Emulate3Buttons" "true"
EndSection

Section "InputDevice"
 Driver "wacom"
 Identifier "stylus"
 Option "Device" "/dev/input/wacom"
 Option "Type" "stylus"
 Option "ForceDevice" "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
 Driver "wacom"
 Identifier "eraser"
 Option "Device" "/dev/input/wacom"
 Option "Type" "eraser"
 Option "ForceDevice" "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
 Driver "wacom"
 Identifier "cursor"
 Option "Device" "/dev/input/wacom"
 Option "Type" "cursor"
 Option "ForceDevice" "ISDV4"# Tablet PC ONLY
EndSection

Section "Device"
 Identifier "nVidia Corporation NV36.2 [GeForce FX 5700]"
 Driver "nvidia"
 Busid "PCI:1:0:0"
 Videoram 256000
EndSection

Section "Monitor"
 Identifier "Generic Monitor"
 Option "DPMS"
 Horizsync 30-100
 Vertrefresh 50-160
EndSection

Section "Screen"
 Identifier "Default Screen"
 Device "nVidia Corporation NV36.2 [GeForce FX 5700]"
 Monitor "Generic Monitor"
 Defaultdepth 24
 SubSection "Display"
  Modes "1280x1024" "1024x768" "800x600" "640x480"
 EndSubSection
 Option "AddARGBGLXVisuals" "True"
 Option "UseEdidFreqs" "false"
EndSection

Section "ServerLayout"
 Identifier "Default Layout"
  screen "Default Screen"
 Inputdevice "Generic Keyboard"
 Inputdevice "Configured Mouse"

 # Uncomment if you have a wacom tablet
 # InputDevice "stylus" "SendCoreEvents"
 # InputDevice "cursor" "SendCoreEvents"
 # InputDevice "eraser" "SendCoreEvents"
EndSection
Section "Extensions"
 Option "Composite" "Enable"
EndSection

Thanks in advance.

---

### Post by hhhhhx on 2008-03-15
does your video card support that resolution?

---

### Post by rwakefie on 2008-03-15
It does, I have been running windows vista ultimate for about 6 months on that resolution; maybe the driver for Linux does not, I will have to look into that.
Thanks

---

