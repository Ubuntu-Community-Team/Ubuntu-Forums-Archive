---
title: "Poor 2D performance w/o xserver-xgl, poor 3D w/ xserver-xgl ?!?"
date: 2008-03-21
forum: Absolute Beginner Talk
---

### Post by Mikersoft on 2008-03-21
Hello, I've been using Ubuntu for a week now, I'm running an Inspiron w/ an nVidia 8600M GT card, with the driver courtesy of Envy.

Without the xserver-xgl package installed, I can access nVidia settings and I have good 3D performance (14000+ fps on glxgears). However, 2D effects lag, such as minimizing/maximizing windows, or even rendering images as I'm scrolling down a webpage :-\

With xserver-xgl, my 2D performance is much, much improved, and I have many of the minimize/maximize/close animations in the Animations plugin in Compiz enabled, and they are quite smooth, as is interweb browsing :) But nvidia-settings doesn't work, and glxinfo says direct rendering is off. glxgears also gives me about ~10000 fps now. 

Also, I tried a 3D game, nexuiz, which isn't as good looking as Quake 3, gives me ~20fps, while on my XP I can run FEAR maxed out at just about the same resolution. Oh, and I havent tried this game while not running xserver-xgl.

Can anybody help me? I don't want to uninstall xserver-xgl whenever I want 3D performance, and reinstall it when I want 2D performance. For one thing, I can't while I'm at my boarding school without the interwebz (grrr). I can post my xorg.conf if it would help. Any advice that can be spared would be greatly appreciated.

---

### Post by FuturePilot on 2008-03-21
With a Nvidia card you don't need XGL. I'm not sure why you are getting bad 2D performance. Perhaps we should look deeper into that. But XGL causes weird problems if you use if with Nvidia. It definitely doesn't play nice with games. (bad pun :lolflag:)

---

### Post by Mikersoft on 2008-03-21
Yeah, I've heard the same from other threads, but I still have terrible 2D performance w/ xserver-xgl. Min/maxing windows is just really choppy, and seems to skip frames. Also, the laggy 2D performance seems to be caused by the process "xorg." It goes to 50%+ CPU usage whenever I manipulate windows.

---

### Post by oedha on 2008-03-21
have you try to use nvidia driver from nvidia itself ?

---

### Post by Mikersoft on 2008-03-21
I have the driver Envy downloaded for me, which I'm fairly certain is the official nVidia driver. It's listed as "nVidia" in xorg.conf.

---

### Post by FuturePilot on 2008-03-21
Yes, Envy does download the driver directly from Nvidia. 
Can you post your xorg.conf?
```
cat /etc/X11/xorg.conf
```

---

### Post by Mikersoft on 2008-03-21
> 
Section "ServerLayout"

	# Uncomment if you have a wacom tablet
	#	InputDevice     "stylus"	"SendCoreEvents"
	#	InputDevice     "cursor"	"SendCoreEvents"
	#	InputDevice     "eraser"	"SendCoreEvents"
    Identifier     "Default Layout"
    Screen         "Default Screen" 0 0
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
    InputDevice    "Synaptics Touchpad"
EndSection

Section "Files"
EndSection

Section "Module"
    Load           "glx"
    Load          "dri"
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
    Identifier     "Synaptics Touchpad"
    Driver         "synaptics"
    Option         "SendCoreEvents" "true"
    Option         "Device" "/dev/psaux"
    Option         "Protocol" "auto-dev"
    Option         "HorizEdgeScroll" "0"
EndSection

Section "InputDevice"
    Identifier     "stylus"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "stylus"
    Option         "ForceDevice" "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
    Identifier     "eraser"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "eraser"
    Option         "ForceDevice" "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
    Identifier     "cursor"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "cursor"
    Option         "ForceDevice" "ISDV4"# Tablet PC ONLY
EndSection

Section "Monitor"
    Identifier     "Generic Monitor"
    HorizSync       28.0 - 84.0
    VertRefresh     43.0 - 60.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "nVidia Corporation G80 [GeForce 8600M GT]"
    Driver         "nvidia"
    Option         "RenderAccel" "True"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "nVidia Corporation G80 [GeForce 8600M GT]"
    Monitor        "Generic Monitor"
    DefaultDepth    24
    Option         "UseFBDev" "true"
    Option         "AddARGBVisuals" "True"
    Option         "NoLogo" "True"
    Option         "AddARGBGLXVisuals" "True"
    SubSection     "Display"
        Depth       24
        Modes      "1680x1050"
    EndSubSection
EndSection

Section "Extensions"
    Option         "Composite" "Enable"
EndSection

Section "DRI"
        Mode    0666
EndSection

There might be some extra, unnecessary lines in there that I put in in hopes of fixing my problem.

---

### Post by Mikersoft on 2008-03-21
I don't know how much this matters, but the xorg.conf I posted above is with xserver-xgl installed. If it would help, I can uninstall xserver-xgl, I can print out xorg.conf without it (which is the way my Ubuntu came).

---

### Post by Mikersoft on 2008-03-22
Bump. I would love to have this problem solved before spring break ends and I get shipped back to prison school.

---

### Post by DSn0wMan on 2008-03-22
You can try some compiz settings to make things a little smoother. In compiz config settings manager go to General Settings -> Display Settings and uncheck Detect refresh rate, and Sync to VBlank. Then set refresh rate to 200.

I would recommend uninstalling not using xserver-xgl

I use an older NVIDIA (FX5500) card but here are the relevant settings that I use. An I get around 40 FPS on Nexuiz

Section "Module"
    Load           "bitmap"
    Load           "dbe"
    Load           "ddc"
    Load           "extmod"
    Load           "freetype"
    Load           "glx"
    Load           "int10"
    Load           "vbe"
EndSection

Section "Device"
    Identifier     "NVIDIA FX5500"
    Driver         "nvidia"
    VendorName     "NVIDIA"
    BoardName      "NVIDIA GeForce FX (generic)"
    BusID          "PCI:1:0:0"
    Screen          0
    Option	   "ModeValidation" "NoEdidDFPMaxSizeCheck"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "NVIDIA FX5500"
    Monitor        "Acer AL1917W"
    DefaultDepth    24
    Option         "AddARGBGLXVisuals" "True"
    Option         "NoLogo" "True"
    SubSection     "Display"
        Depth       1
        Modes      "1440x900" "1280x800" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1440x900" "1280x800" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1440x900" "1280x800" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1440x900" "1280x800" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1440x900" "1280x800" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1440x900" "1280x800" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection

Section "Extensions"
    Option         "Composite" "Enable"
EndSection

---

