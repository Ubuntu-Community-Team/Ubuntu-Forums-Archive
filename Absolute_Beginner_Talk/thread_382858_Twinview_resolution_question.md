---
title: "Twinview resolution question"
date: 2007-03-12
forum: Absolute Beginner Talk
---

### Post by bobicus on 2007-03-12
I've got a NVIDIA GeForce 7300 LE graphics card with 2 identical Dell 1707FP LCD monitors hooked up to it and I'm trying to figure out an issue with twinview where the highest combined resolution where both monitors are active is 2048x768, whereas each individual monitor's resolution can go up to 1280x1024. When I try to set it to that, however, one of the monitors goes blank. Here are the relevant sections of my xorg.conf file:

> Section "ServerLayout"
    Identifier     "Default Layout"
    Screen 0       "Default Screen" 0 0
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
    InputDevice    "stylus" "SendCoreEvents"
    InputDevice    "cursor" "SendCoreEvents"
    InputDevice    "eraser" "SendCoreEvents"
EndSection

Section "Monitor"
    Identifier     "Dell 1707FP"
    HorizSync       28.0 - 51.0
    VertRefresh     43.0 - 60.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "NVIDIA GeForce 7300 LE"
    Driver         "nvidia"
    Option         "NoLogo"
    Option         "TwinView" "True"
    Option         "MetaModes" "1280x1024,1280x1024; 1024x768,1024x768"
    Option         "SecondMonitorHorizSync" "28.0 - 51.0"
    Option         "SecondMonitorVertRefresh" "43.0 - 60.0"
    Option         "ConnectedMonitor" "CRT-0, DFP-0"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "NVIDIA GeForce 7300 LE"
    Monitor        "Dell 1707FP"
    DefaultDepth    24
    Option         "UseFBDev" "true"
    SubSection     "Display"
	Viewport   0 0
        Depth       1
        Modes      "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
	Viewport   0 0
        Depth       4
        Modes      "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
	Viewport   0 0
        Depth       8
        Modes      "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
	Viewport   0 0
        Depth       15
        Modes      "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
	Viewport   0 0
        Depth       16
        Modes      "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
	Viewport   0 0
        Depth       24
        Modes      "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection



What is it that I'm missing here? I don't think its a video card limitation, as both monitors can be at their full resolution under XP.

---

### Post by kerry_s on 2007-03-12
I don"t know if it makes a difference but you missed a spacing->

Option "MetaModes" "1280x1024,1280x1024; 1024x768,1024x768"
should be->
Option "MetaModes" "1280x1024, 1280x1024; 1024x768, 1024x768"

I would dump the setting you don't want.

Option "MetaModes" "1280x1024, 1280x1024"


You could try tricking it with the panning featutre->

Option "MetaModes" "1024x768 @1280x1024, 1024x768 @1280x1024"
or
Option "MetaModes" "1280x1024 @1280x1024, 1280x1024 @1280x1024"

Check you /var/log/Xorg.0.log for the (EE)<errors that might help you figure things out.

Also this part->
Option "ConnectedMonitor" "CRT-0, DFP-0"
Is your second monitor the tv?

---

