---
title: "Multiple Monitors"
date: 2007-07-20
forum: Absolute Beginner Talk
---

### Post by therightclique on 2007-07-20
I apologize if this is a retread for anyone. I'm fairly new to linux in general, but not at all new to computers.

I'm building a new system and I have two flat screen LCD displays. one is a samsung. the other is an acer. 

i've just installed ubuntu ultimate 1.4 (based on feisty fawn) and i'm having trouble with multiple displays.

i'm currently using a geforce fx 5200, with 2 VGA outputs. not a great card, but its all i could afford at the time. the rest of the system is pretty good by comparison.

ubuntu ultimate 1.4 comes with something called Envy, which installed NVIDIA drivers for me.It also installed "nvidia settings" under system tools. 

i've used NVIDIA SETTINGS to enable my second display (in this case, the acer lcd). 

i do get it to display on both monitors in "twinview" but the acer is only running at 640x480 and the samsung at 1280x1024. i'd prefer them to both be 1280.  the NVIDIA SETTINGS window only gives me 640x480 and some 320x option. 

if anyone can at least point me in the right direction, i'll be grateful. thanks. i've included my xorg.conf just in case that helps. it sorta looks like the conf file is not even recognizing my other display at all, despite the fact that it is up and running right now. the samsung is working fine, but the acer is still at 640. is there not a straight forward config option for this type of thing? at least one thing XP has right. 

```
Section "ServerLayout"
    Identifier     "Default Layout"
    Screen         "Default Screen" 0 0
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
    InputDevice    "stylus" "SendCoreEvents"
    InputDevice    "cursor" "SendCoreEvents"
    InputDevice    "eraser" "SendCoreEvents"
EndSection

Section "Files"

	# path to defoma fonts
    FontPath        "/usr/share/fonts/X11/misc"
    FontPath        "/usr/share/fonts/X11/cyrillic"
    FontPath        "/usr/share/fonts/X11/100dpi/:unscaled"
    FontPath        "/usr/share/fonts/X11/75dpi/:unscaled"
    FontPath        "/usr/share/fonts/X11/Type1"
    FontPath        "/usr/share/fonts/X11/100dpi"
    FontPath        "/usr/share/fonts/X11/75dpi"
    FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
    Load           "i2c"
    Load           "bitmap"
    Load           "ddc"
    Load           "extmod"
    Load           "freetype"
    Load           "glx"
    Load           "int10"
    Load           "vbe"
EndSection

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "CoreKeyboard"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc105"
    Option         "XkbLayout" "us"
EndSection

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ImPS/2"
    Option         "ZAxisMapping" "4 5"
    Option         "Emulate3Buttons" "true"
EndSection

Section "InputDevice"
    Identifier     "stylus"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "stylus"
    Option         "ForceDevice" "ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
    Identifier     "eraser"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "eraser"
    Option         "ForceDevice" "ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
    Identifier     "cursor"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "cursor"
    Option         "ForceDevice" "ISDV4"		# Tablet PC ONLY
EndSection

Section "Monitor"
    Identifier     "SyncMaster"
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "nVidia Corporation NV34 [GeForce FX 5200]"
    Driver         "nvidia"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "nVidia Corporation NV34 [GeForce FX 5200]"
    Monitor        "SyncMaster"
    DefaultDepth    24
    SubSection     "Display"
        Depth       1
        Modes      "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
EndSection

Section "Extensions"
    Option         "Composite" "Enable"
EndSection
```

---

### Post by kidcharles on 2007-07-20
I culled this section of code from:

[http://www.yolinux.com/TUTORIALS/LinuxAndDualMonitors.html](http://www.yolinux.com/TUTORIALS/LinuxAndDualMonitors.html)

You can try adding some or all of the options under the "Device" section in your xorg.conf file. I think the key option is the "Meta Modes" section. I'm no expert on this, but I think the pairs of resolutions (like "1280x1024,1280x1024") are the resolutions for each monitor. The pairs are then separated by semi-colons in case you want to make other resolutions available.

```

Section "Device"
        Identifier  "Videocard0"
        Driver      "nvidia"
        VendorName  "Videocard vendor"
        BoardName   "NVIDIA Quadro 4 (generic)"
        Option	    "TwinView" "true"
        Option	    "TwinViewOrientation" "RightOf"
        Option	    "SecondMonitorHorizSync" "31-81"
        Option	    "SecondMonitorVertRefresh" "55-85"
        Option	    "MetaModes" "1280x1024,1280x1024; 1024x768,1024x768"
        Option	    "ConnectedMonitor" "FPD,FPD"
EndSection

```

---

