---
title: "I need help with XrandR and S-Video"
date: 2007-11-27
forum: Apple Intel Users
---

### Post by Teh Dust on 2007-11-27
A month ago I got a MacBook and decided to dual boot Ubuntu 7.10 with it. I am now trying to copy my laptops screen to my Sanyo TV. I bought the mini dvi to video adapter and have the TV connected to the laptop via S-video. I have tried every guide I could find but have not succeeded in getting any type of picture on my TV. When I type a XrandR command into terminal my TV flickers and thats it.

This is my XrandR output.
```
Screen 0: minimum 320 x 200, current 1280 x 800, maximum 2080 x 2080
VGA connected (normal left inverted right)
        Identifier: 0x43
        Timestamp:  -2076211329
        Subpixel:   unknown
        Clones:    
        CRTCs:      0 1
        EDID_DATA:
                00ffffffffffff000610089d01010101
                070c0103100000963067a9a056479926
                11484c00006101010101010101010101
                01010101010101010101010101010101
                01010101010101010101010101010101
                01010101010101010101010101010101
                010101010101010101010101000000fc
                004e5453432f50414c0a202020200038
  1280x800 (0x47)   83.5MHz
        h: width  1280 start 1344 end 1480 total 1680 skew    0 clock   49.7KHz
        v: height  800 start  801 end  804 total  828           clock   60.0Hz
  1280x768 (0x48)   80.1MHz
        h: width  1280 start 1344 end 1480 total 1680 skew    0 clock   47.7KHz
        v: height  768 start  769 end  772 total  795           clock   60.0Hz
  1024x768 (0x49)   65.0MHz -HSync -VSync
        h: width  1024 start 1048 end 1184 total 1344 skew    0 clock   48.4KHz
        v: height  768 start  771 end  777 total  806           clock   60.0Hz
  800x600 (0x4a)   40.0MHz +HSync +VSync
        h: width   800 start  840 end  968 total 1056 skew    0 clock   37.9KHz
        v: height  600 start  601 end  605 total  628           clock   60.3Hz
  640x480 (0x4b)   25.2MHz -HSync -VSync
        h: width   640 start  656 end  752 total  800 skew    0 clock   31.5KHz
        v: height  480 start  490 end  492 total  525           clock   59.9Hz
LVDS connected 1280x800+0+0 (0x4c) normal (normal left inverted right) 286mm x 179mm
        Identifier: 0x44
        Timestamp:  -2076211329
        Subpixel:   horizontal rgb
        Clones:    
        CRTC:       1
        CRTCs:      1
        EDID_DATA:
                00ffffffffffff0006105b9c00000000
                0e100103801d12780a87f594574f8c27
                27505400000001010101010101010101
                010101010101bc1b00a0502017303020
                36001eb3100000190000000100061020
                00000000000000000a20000000fe004c
                544e31333357310000000a20000000fc
                00436f6c6f72204c43440a20202000c6
        BACKLIGHT_CONTROL: 0 (0x00000000) range:  (0,4)
        BACKLIGHT: 230 (0x000000e6) range:  (0,296)
  1280x800 (0x4c)   71.0MHz -HSync -VSync
        h: width  1280 start 1328 end 1360 total 1440 skew    0 clock   49.3KHz
        v: height  800 start  803 end  809 total  823           clock   59.9Hz
  1280x800 (0x47)   83.5MHz
        h: width  1280 start 1344 end 1480 total 1680 skew    0 clock   49.7KHz
        v: height  800 start  801 end  804 total  828           clock   60.0Hz
  1280x768 (0x48)   80.1MHz
        h: width  1280 start 1344 end 1480 total 1680 skew    0 clock   47.7KHz
        v: height  768 start  769 end  772 total  795           clock   60.0Hz
  1024x768 (0x49)   65.0MHz -HSync -VSync
        h: width  1024 start 1048 end 1184 total 1344 skew    0 clock   48.4KHz
        v: height  768 start  771 end  777 total  806           clock   60.0Hz
  800x600 (0x4a)   40.0MHz +HSync +VSync
        h: width   800 start  840 end  968 total 1056 skew    0 clock   37.9KHz
        v: height  600 start  601 end  605 total  628           clock   60.3Hz
  640x480 (0x4b)   25.2MHz -HSync -VSync
        h: width   640 start  656 end  752 total  800 skew    0 clock   31.5KHz
        v: height  480 start  490 end  492 total  525           clock   59.9Hz
TMDS-1 connected 1280x800+0+0 (0x47) normal (normal left inverted right) 0mm x 0mm
        Identifier: 0x45
        Timestamp:  -2076211329
        Subpixel:   horizontal rgb
        Clones:    
        CRTC:       0
        CRTCs:      0 1
  1280x800 (0x47)   83.5MHz
        h: width  1280 start 1344 end 1480 total 1680 skew    0 clock   49.7KHz
        v: height  800 start  801 end  804 total  828           clock   60.0Hz
  1280x768 (0x48)   80.1MHz
        h: width  1280 start 1344 end 1480 total 1680 skew    0 clock   47.7KHz
        v: height  768 start  769 end  772 total  795           clock   60.0Hz
  1024x768 (0x49)   65.0MHz -HSync -VSync
        h: width  1024 start 1048 end 1184 total 1344 skew    0 clock   48.4KHz
        v: height  768 start  771 end  777 total  806           clock   60.0Hz
  800x600 (0x4a)   40.0MHz +HSync +VSync
        h: width   800 start  840 end  968 total 1056 skew    0 clock   37.9KHz
        v: height  600 start  601 end  605 total  628           clock   60.3Hz
  640x480 (0x4b)   25.2MHz -HSync -VSync
        h: width   640 start  656 end  752 total  800 skew    0 clock   31.5KHz
        v: height  480 start  490 end  492 total  525           clock   59.9Hz
TV disconnected (normal left inverted right)
        Identifier: 0x46
        Timestamp:  -2076211329
        Subpixel:   unknown
        Clones:    
        CRTCs:      0 1
        BOTTOM: 37 (0x00000025) range:  (0,100)
        RIGHT: 46 (0x0000002e) range:  (0,100)
        TOP: 36 (0x00000024) range:  (0,100)
        LEFT: 54 (0x00000036) range:  (0,100)
        TV_FORMAT: NTSC-M
                supported: NTSC-M       NTSC-443     NTSC-J       PAL-M       
                           PAL-N        PAL          480p@59.94Hz 480p@60Hz   
                           576p         720p@60Hz    720p@59.94Hz 720p@50Hz   
                           1080i@50Hz   1080i@60Hz   1080i@59.94H

```

This is my xorg.conf
```
# xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
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
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizEdgeScroll"	"0"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"stylus"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"eraser"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"cursor"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller"
	Driver		"intel"
	BusID		"PCI:0:2:0"
EndSection

Section "Monitor"
	Identifier	"Color LCD"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller"
	Monitor		"Color LCD"
	DefaultDepth	24
	SubSection "Display"
		Depth	24
		Virtual	2080	2080
		Modes		"1280x800" "800x600"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"

# Uncomment if you have a wacom tablet
#	InputDevice     "stylus"	"SendCoreEvents"
#	InputDevice     "cursor"	"SendCoreEvents"
#	InputDevice     "eraser"	"SendCoreEvents"
	InputDevice	"Synaptics Touchpad"
EndSection
```

Any help would be greatly appreciated.

---

### Post by nielsb on 2007-11-28
The output you post above, is that when you have your TV connected through the mini DVI and S?

If so, what happens if you do something like so:

```
xrandr --output VGA --auto
```

Niels

---

### Post by Teh Dust on 2007-11-28
Yes, that is with my TV plugged in.

When I put in the command, the screen flickers for a slight second but stays blank.

---

### Post by cyberdork33 on 2007-11-28
[http://www.thinkwiki.org/wiki/Xorg_RandR_1.2](http://www.thinkwiki.org/wiki/Xorg_RandR_1.2)

Try setting a mode on the screen manually.
```
xrandr --output VGA --mode 0x47
```

---

### Post by Teh Dust on 2007-11-28
I still get only get the TV to flicker for a moment.

When I use VGA I get the error
```
xrandr: cannot find crtc for output VGA

```

One guide said that the output should be on TMDS-1. When I try to set the resolution manually for TMDS-1 my panels are resized to the resolution but stay on my laptops screen.

---

### Post by nielsb on 2007-11-28
> **Teh Dust said:**
> Yes, that is with my TV plugged in.

When I put in the command, the screen flickers for a slight second but stays blank.

Then as cyberdork33 suggests input mode(s) directly.

First do a:

```
xrandr -q
```

that will show you the various "supported" modes. Then you can try each explicitly by:

```
xrandr --output VGA --mode 1024x768
```

etc, and see if any works.

Niels

---

### Post by Teh Dust on 2007-11-28
With VGA
```
xrandr: cannot find crtc for output VGA

```

With LVDS
My laptops resolution changes

With TMDS-1
My panels resolution changes

With TV
```
xrandr: cannot find mode 1024x768

```

---

### Post by cyberdork33 on 2007-11-28
> **Teh Dust said:**
> 
With TV
```
xrandr: cannot find mode 1024x768

```
That is not one of the modes listed for TV...

I have never used it with a tv before, so I don't know the specifics. I didn't quite understand how you have the TV hooked up though. You have a converter connected to your DVI port that converts to S-video? Are you sure this is working correctly? Can you try it under OSX?

---

### Post by Teh Dust on 2007-11-28
Yes, it works in OSX.

In XrandR, TV is disconnected with mine as well as everyone else who owns a MacBook (as far as I have seen)

The tv is connected through a cable that converts mini dvi to s-video, in XrandR it is TMDS-1

This is the cable that I am using. The box has Video and S-video, I have tried both and can get nothing to work.
[http://store.apple.com/1-800-MY-APPLE/WebObjects/AppleStore.woa/wa/RSLID?mco=A9ADA2DA&fnode=home/shop_mac/mac_accessories/cables&nplm=M9319G/A]("http://store.apple.com/1-800-MY-APPLE/WebObjects/AppleStore.woa/wa/RSLID?mco=A9ADA2DA&fnode=home/shop_mac/mac_accessories/cables&nplm=M9319G/A")

---

### Post by willskills on 2007-12-10
Hi Teh Dust, I might be able to shed a little light on the situation.

I am currently using xrandr to output to my TV through s-video, using an S-video to RCA adaptor, and it's working alright. S-video reports as disconnected, but I still can view stuff on the TV.

simply try;

xrandr --addmode S-video 800x600

then 

xrandr --output S-video --mode 800x600

The only thing I'm struggling with is changing the actual size of the display, as the right hand side of display is not visible on the tv. I am guessing I need to play with the Hsync and Vsync, but I'm a bit stuck, not quite sure how to do so. Can anyone shed any light on the situation? :)

Thanks!

---

### Post by cyberdork33 on 2007-12-11
you can try with the s-video output, but I think you are techincally using the DVI output...

---

