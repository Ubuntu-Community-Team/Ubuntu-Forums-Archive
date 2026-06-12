---
title: "xorg.conf Mysteries"
date: 2008-02-01
forum: Absolute Beginner Talk
---

### Post by imaginal on 2008-02-01
So, I have some laptop issues and I think some tinkering in xorg.conf might help my case. Problem is, I'm not full of xorg knowledge. Questions:

1. Where can I find a list of options for the xorg.conf? man xorg.conf helped some, but didn't tell me anything when it came to synaptics.

2. My touchpad is really sluggish. If I delete the synaptics entry in xorg.conf, it treats my touchpad like any other mouse. Sensitivity is perfect, but I loose vertical scrolling and double tapping: stuff that synaptics is there for. How do I make this better?

3. I've been [battling]("http://ubuntuforums.org/showthread.php?t=661501") with some monitor issues. Moving things look great in vista, but have noticeable horizontal lines in 7.10. My guess is monitor refresh/horizontal scrolling something... How do I learn what I need to do to fix this?

Thanks again for your patience!!! I'm very grateful for everything this forum has provided!

---

### Post by intel on 2008-02-01
Taken From http://www.cs.utexas.edu/~erkin/home/tools/xorg.conf

```

# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# Edit this file with caution, and see the /etc/X11/xorg.conf manual page.
# (Type "man /etc/X11/xorg.conf" at the shell prompt.)

Section "ServerLayout"
	Identifier     "Default Layout"
	Screen         "Default Screen" 0 0
	Screen         "aticonfig-Screen[1]" RightOf "Default Screen"
	InputDevice    "Generic Keyboard"
	InputDevice    "Configured Mouse" "SendCoreEvents"
	InputDevice    "Synaptics Touchpad" "CorePointer"
	Option	    "Clone" "off"
	Option	    "Xinerama" "off"
	# Option      "OffTime" "3"
EndSection

Section "Files"

	# path to defoma fonts
	FontPath     "/usr/share/X11/fonts/misc"
	FontPath     "/usr/share/X11/fonts/cyrillic"
	FontPath     "/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath     "/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath     "/usr/share/X11/fonts/Type1"
	FontPath     "/usr/share/X11/fonts/100dpi"
	FontPath     "/usr/share/X11/fonts/75dpi"
	FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load  "i2c"
	Load  "bitmap"
	Load  "ddc"
	Load  "dri"
	Load  "extmod"
	Load  "freetype"
	Load  "glx"
	Load  "int10"
	Load  "type1"
	Load  "vbe"
EndSection

Section "ServerFlags"
	Option	    "AllowMouseOpenFail"
# Resize and Rotate extension, allows screen geometry changes on the fly.
	Option	    "RandR" "on"
	Option	    "blank time" "30"
	Option	    "standby time" "30"
	Option	    "suspend time" "30"
	Option	    "off time" "40"
EndSection

Section "InputDevice"
	Identifier  "Generic Keyboard"
	Driver      "kbd"
	Option	    "CoreKeyboard"
	Option	    "XkbRules" "xorg"
	Option	    "XkbModel" "pc104"
	Option	    "XkbLayout" "us"
EndSection

Section "InputDevice"
	Identifier  "Configured Mouse"
	Driver      "mouse"
	Option	    "Device" "/dev/input/mice"
	Option	    "Protocol" "ExplorerPS/2"
	Option	    "Emulate3Buttons" "true"
EndSection

Section "InputDevice"

	# Outer			(52,46-995,728)	Observed bounding box
	# Probably really	(0,0-1000,750)	Bezel covers some active area
	# Inner			(100,100-950,670) Outside this is a corner tap
	# speed: MinSpeed if slow, MaxSpeed if fast.  With driver 0.13.5,
	# units were different and 0.65, 0.15 were my preferred values.
	# A = AccelFactor.  Then dS = A * dP * dP but limited by 
	# {Min,Max}Speed * dP.  Packets come out a time dT apart, where we can 
	# only guess what dT is.  Empirically, A = 0.05 gives a speed of about 
	# 1.0, i.e. 1 pixel per pad unit, if you cross the pad in 1 second.
	# packets, scrolling continues until you tap.  0 -> disable.
	# Alps pad poorly gives Z (compared to Synaptics), so this scaling
	# is not used.  Speed may be screen pixels/sec.
	# tap inside with N fingers.  0 -> nothing, 1 = left button, 
	# 2 = middle button, 3 = right button.  The Alps pad cannot distinguish
	# multiple fingers.
	# Unlike the Synaptics pad, on a tap the Alps pad sends one single
	# packet (hardware detection) with Z=16 followed 100 msec later by one 
	# in the exact same place with Z=0.  (Never < 90 msec, always < 110
	# msec.)  (There's a kernel patch to kludge around this.)
	# In order for a tap to be recognized:
	# Touch and release must be no more distant than this (pad units)
	# NOTE! Change to 210 with Alps hardware tap patch mentioned above.
	# jimc uses 110 without the patch.
	# be long enough so you can see the button change color.
	# edge, 2 = top right corner, etc. around the edge of the pad up to
	# 8 = top left corner.
	Identifier  "Synaptics Touchpad"
	Driver      "synaptics"
	Option	    "InputFashion" "Mouse"
	Option	    "Name" "AlpsPS/2 ALPS TouchPad"
	Option	    "Vendor" "Sysp"
	Option	    "Protocol" "imps/2"
	Option	    "Device" "/dev/input/mice"
	Option	    "Buttons" "8"
	Option	    "ZAxisMapping" "4 5 6 7"
	# Allows synclient to configure the driver in real time.
	Option	    "SHMConfig" "on"
	# Corners of Alps Glidepoint touchpad: 
	Option	    "TopEdge" "250"
	Option	    "BottomEdge" "600"
	Option	    "LeftEdge" "100"
	Option	    "RightEdge" "860"
	# "Speeds" are in screen pixels per pad unit.  Ratio scales with finger
	Option	    "MaxSpeed" "0.8"
	Option	    "MinSpeed" "0.4"
	# dS = change in screen pixels; dP = change in pad units per "packet"; 
	Option	    "AccelFactor" "0.03"
	# X or Y pad motion for each scroll event (simulated button)
	Option	    "VertScrollDelta" "25"
	Option	    "HorizScrollDelta" "25"
        # If scroll speed (events/sec) is above this value for 4 successive
	Option	    "CoastingSpeed" "3.0"
	# Edge motion speed scales with Z axis (pressure).  However, the
	Option	    "EdgeMotionMinZ" "65"
	Option	    "EdgeMotionMaxZ" "80"
	Option	    "EdgeMotionMinSpeed" "150"
	Option	    "EdgeMotionMaxSpeed" "150"
	# True -> use for normal movement, false -> only for dragging.
	Option	    "EdgeMotionUseAlways" "off"
	# What happens when you tap the {Left,Right}{Top,Bottom} corner or
	Option	    "LBCornerButton" "0"
	Option	    "LTCornerButton" "0"
	Option	    "RBCornerButton" "3"
	Option	    "RTCornerButton" "2"
	Option	    "TapButton1" "1"
	Option	    "TapButton2" "2"
	Option	    "TapButton3" "3"
	# If Z axis is above FingerHigh -> touch.  Below FingerLow -> release.
	Option	    "FingerHigh" "15"
	Option	    "FingerLow" "10"
	# (Note: defaults for the next 3 come out to 220 180 180 for Synaptics)
	Option	    "MaxTapMove" "200"
	# Release must follow touch no longer than this (msec)
	Option	    "MaxTapTime" "210"
	Option	    "FastTaps" "1"
	# Second tap must follow release this closely to recognize double tap.
	Option	    "MaxDoubleTapTime" "150"
	# How long between emulated button-down and button-up events.  Should
	Option	    "ClickTime" "100"
	# If physical buttons 1 and 3 are hit within this time, do button 2.
	Option	    "EmulateMidButtonTime" "150"
	# 0 = enable, 1 = disable completely, 2 = only tapping is disabled
	Option	    "TouchpadOff" "0"
	# On -> drag continues until you tap a second time.
	Option	    "LockedDrags" "off"
# These features are not turned on.
	Option	    "GuestMouseOff" "off"
	Option	    "CircularScrolling" "off"
	# Angle in radians for each scroll event
	Option	    "CircScrollDelta" "0.2"
	# Where do you touch to start circular scroll?  0 -> any edge, 1 = top 
	Option	    "CircScrollTrigger" "0"
	Option	    "PalmDetect" "off"
EndSection

Section "Monitor"
	Identifier   "Generic Monitor"
	Option	    "DPMS" "true"
	DisplaySize 331.7 207.314
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[1]"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
#	Option	    "VideoOverlay" "on"
#	Option	    "OpenGLOverlay" "off"
	Identifier  "ATI Technologies, Inc. M22 [Radeon Mobility M300]"
	Driver      "fglrx"
	Option	    "UseInternalAGPGART" "no"
	Option	    "KernelModuleParm" "agplock=0"
#	Option		"mtrr" "off" # disable DRI mtrr mapper
#	Option      "RenderAccel" "True"
#	Option      "TripleBuffer" "true"
	Option	    "DesktopSetup" "mirror"
	Option	    "TVFormat" "NTSC-M"
	Option	    "TVStandard" "VIDEO"
	Option	    "HSync2" "30-81"
	Option	    "VRefresh2" "56-88"
	Option	    "OverlayOnCRTC2" "1"
	Option	    "EnableMonitor" "tv"
#	Option	    "ForceMonitors" "tv"
	BusID       "PCI:1:0:0"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[1]"
	Driver      "fglrx"
	BusID       "PCI:1:0:0"
	Screen      1
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device     "ATI Technologies, Inc. M22 [Radeon Mobility M300]"
	Monitor    "Generic Monitor"
	DefaultDepth     24
	SubSection "Display"
		Depth     1
		Modes    "1680x1050"
	EndSubSection
	SubSection "Display"
		Depth     4
		Modes    "1680x1050"
	EndSubSection
	SubSection "Display"
		Depth     8
		Modes    "1680x1050"
	EndSubSection
	SubSection "Display"
		Depth     15
		Modes    "1680x1050"
	EndSubSection
	SubSection "Display"
		Depth     16
		Modes    "1680x1050"
	EndSubSection
	SubSection "Display"
		Depth     24
		Modes    "1680x1050"
	EndSubSection
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[1]"
	Device     "aticonfig-Device[1]"
	Monitor    "aticonfig-Monitor[1]"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

Section "DRI"
	Mode         0666
EndSection

Section "Extensions"
	Option	    "Composite" "0"
EndSection


```

---

### Post by oedha on 2008-02-01
may i ?
you can find xorg.conf :==> /etc/X11/xorg.conf

or if you want to set it up again :==> sudo dpkg-reconfigure xserver-xorg
answer or fill the questions...based on your comp specification.......

regards;
~E~

---

### Post by erfahren on 2008-02-01
for your touchpad there's a couple of programs available in the repositories that may have additional options to configure it - gSynaptics and qSynaptics - you might try one of them 

to use either of them you need to add a line in the xorg.conf under the Synaptics section that is:
```

Option          "SHMConfig"             "on"

```
(it just allows additional configurations to be handled in shared memory if needed - the way I understand it anyway)

you can see the man page for additional configuration options: [http://linux.die.net/man/5/synaptics](http://linux.die.net/man/5/synaptics)
also the Gentoo wiki page on it: [http://gentoo-wiki.com/HARDWARE_Synaptics_Touchpad](http://gentoo-wiki.com/HARDWARE_Synaptics_Touchpad)
also: [xorg.conf & SHMConfig for Synaptics Touchpad](http://ubuntuforums.org/showthread.php?t=168581)


As for your video - I can just post some links to some pages that might help 
(NOTE: I've read (on the Gentoo wiki page - link below) that you don't want to manually add the resolutions unless you know what they should be. It can be bad for the monitor.
[https://help.ubuntu.com/community/FixVideoResolutionHowto](https://help.ubuntu.com/community/FixVideoResolutionHowto)
[Howto: change resolution/refresh rate in Xorg](http://ubuntuforums.org/showthread.php?t=83973)
[http://www.gentoo.org/doc/en/xorg-config.xml](http://www.gentoo.org/doc/en/xorg-config.xml)

---

