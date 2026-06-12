---
title: "nvidia 6600 direct rendering: no"
date: 2007-04-22
forum: Absolute Beginner Talk
---

### Post by xboxbman on 2007-04-22
I just installed Feisty.  It's very nice.  Everything seems to work, except I can't seem to get direct rendering enabled.  I try ```
glxinfo | grep direct
``` and it tells me>  direct rendering: no.  Any one have any ideas as to what I should do?  Under Restricted Drivers Manager (great feature)  It says I'm using the NVIDIA accelerated graphics driver.  I tried some app called Ervy.  I could no longer boot to my desktop thanks to it, but I fixed that.  I dunno what to do about this, I hope someone does...

---

### Post by orb9220 on 2007-04-22
Copy and paste your xorg.conf here.

---

### Post by Malta paul on 2007-04-22
I have a Nvidia 6600 card and have direct rendering.
Try Systems >>Administration>>Restricted drivers manager,    Tick Enable on Nvidia drivers.
Hope this helps :)

---

### Post by xboxbman on 2007-04-22
> **Malta paul said:**
> I have a Nvidia 6600 card and have direct rendering.
Try Systems >>Administration>>Restricted drivers manager,    Tick Enable on Nvidia drivers.
Hope this helps :)
Nvidia is already enabled. Here's my xorg.xonf

```
Section "Files"
	Fontpath	"/usr/share/fonts/X11/misc"
	Fontpath	"/usr/share/fonts/X11/cyrillic"
	Fontpath	"/usr/share/fonts/X11/100dpi/:unscaled"
	Fontpath	"/usr/share/fonts/X11/75dpi/:unscaled"
	Fontpath	"/usr/share/fonts/X11/Type1"
	Fontpath	"/usr/share/fonts/X11/100dpi"
	Fontpath	"/usr/share/fonts/X11/75dpi"
	# path to defoma fonts
	Fontpath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load		"bitmap"
	Load		"ddc"
	Load		"extmod"
	Load		"freetype"
	Load		"glx"
	Load		"int10"
	Load		"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc104"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"	"/dev/input/mice"
	Option		"Protocol"	"ImPS/2"
	Option		"ZAxisMapping"	"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"stylus"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"eraser"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"cursor"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"nVidia Corporation NV43 [GeForce 6600 GT]"
	Driver		"nvidia"
	Busid		"PCI:1:0:0"
	Option		"AddARGBVisuals"	"True"
	Option		"AddARGBGLXVisuals"	"True"
	Option		"NoLogo"	"True"
EndSection

Section "Monitor"
	Identifier	"DELL 1703FP"
	Option		"DPMS"
	Horizsync	30-70
	Vertrefresh	50-160
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"nVidia Corporation NV43 [GeForce 6600 GT]"
	Monitor		"DELL 1703FP"
	Defaultdepth	24
	SubSection "Display"
		Depth	1
		Modes		"1280x1024"	"1152x864"	"1024x768"	"800x600"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	4
		Modes		"1280x1024"	"1152x864"	"1024x768"	"800x600"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	8
		Modes		"1280x1024"	"1152x864"	"1024x768"	"800x600"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	15
		Modes		"1280x1024"	"1152x864"	"1024x768"	"800x600"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	16
		Modes		"1280x1024"	"1152x864"	"1024x768"	"800x600"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	24
		Modes		"1280x1024"	"1152x864"	"1024x768"	"800x600"	"640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen "Default Screen"
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
	Inputdevice	"stylus"	"SendCoreEvents"
	Inputdevice	"cursor"	"SendCoreEvents"
	Inputdevice	"eraser"	"SendCoreEvents"
EndSection

Section "DRI"
	Mode	0666
EndSection
```


some more problems have arisen.  It seems when ever the screensaver comes on, doesn't matter which one including blank screen, ubuntu crashes.  I imagine this has something to do with the Nvidia card.  One other thing is that on edgy, right before the Ubuntu log in screen came up, there would be an nividia splash screen.  With Feisty, it isn't there.  Thanks for helping.

---

### Post by orb9220 on 2007-04-22
> Option		"AddARGBGLXVisuals"	"True"

Put a comment symbol in front of that line #

# Option		"AddARGBGLXVisuals"	"True"

save then Ctrl-Alt-Backspace to restart x

May not work but I have never seen

Option		"AddARGBVisuals"	"True"
Option		"AddARGBGLXVisuals"	"True"

At the same time in an xorg file.
The first one is what I use.

---

### Post by xboxbman on 2007-04-22
> **orb9220 said:**
> Put a comment symbol in front of that line #

# Option		"AddARGBGLXVisuals"	"True"

save then Ctrl-Alt-Backspace to restart x

May not work but I have never seen

Option		"AddARGBVisuals"	"True"
Option		"AddARGBGLXVisuals"	"True"

At the same time in an xorg file.
The first one is what I use.

Thanks...but it didn't work.  I got the nvidia splash back.  Turns out it was just an option set in xorg.conf.  Still, no direct rendering.

---

### Post by orb9220 on 2007-04-22
Here my section

> Section "Device"
	Identifier	"NVIDIA Corporation NV34 [GeForce FX 5200]"
	Driver		"nvidia"
	BusID		"PCI:2:0:0"
	Option		"TwinView" "on"
        Option          "NvAGP" "3"
	Option		"MetaModes" "1280x1024,1280x1024; 1280x1024,NULL; 1024x768,1024x768; 1024x768,NULL"
	Option		"SecondMonitorHorizSync" "30-70"
	Option		"SecondMonitorVertRefresh" "60"
	Option		"TwinViewOrientation" "RightOf"		
	Option		"ConnectedMonitor" "CRT,CRT"
	Option 		"AllowGLXWithComposite" "true"
	Option		"RenderAccel" "true"
EndSection

Section "Monitor"
	Identifier	"A75f"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NV34 [GeForce FX 5200]"
	Monitor		"A75f"
	DefaultDepth	24
        Option         "AddARGBGLXVisuals" "True"
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1024x768" "800x600" "720x400" "640x480" "640x350"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		0 "Default Screen" 0 0
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
EndSection

Section "DRI"
	Group	0
	Mode	0666
EndSection

Section "Extensions"
          Option  "Composite" "Enable"
EndSection

Hope it helps

---

### Post by xboxbman on 2007-04-22
> **orb9220 said:**
> Here my section



Hope it helps

Thank you for the quick responding.  Unfortunately, I'm still a total noob at Linux, I've only been using Ubuntu for 8 months so far, and thus your xorg.conf might as well be arabic.  I do appreciate you attempts to help.

---

### Post by leg on 2007-04-22
Open synaptic and check if you have mesa installed I have the following installed
```

libgl1-mesa-dri
libgl1-mesa-dev
libgl1-mesa-glx

```
mesa provides dri for your system. You probably don't need the dev one though. Also you can uncomment the line orb9220 had you comment as I have it and mine works fine.
```

Section "Device"
	Identifier	"nVidia Corporation NV34 [GeForce FX 5200]"
	Driver		"nvidia"
	Busid		"PCI:1:0:0"
	Option		"AddARGBVisuals"	"True"
	Option		"AddARGBGLXVisuals"	"True"
	Option		"NoLogo"	"True"
EndSection

```
My module section only has one line that you don't
```
Load		"i2c"
``` but I am not sure if that will help you. I also have this at the very end of my xorg.conf file:```
Section "DRI"
	Mode	0666
EndSection
```

Have fun and hope this helps.

---

### Post by annda on 2007-04-22
i believe you need the GLX extension with this option:

Option "AddARGBGLXVisuals" "True"

it's in orb9220's xorg file, too. i think he meant the other line should be commented out.

---

### Post by xboxbman on 2007-04-22
I checked and mesa is already installed.

I'm afraid none of that made a difference.  Still no direct rendering.

---

### Post by xboxbman on 2007-04-23
bump

---

### Post by xtreme35967 on 2007-04-23
I would try using the new Nvidia Drivers.     nvidia-glx-new    These are the ones that I am using with my 7600GT

---

### Post by xboxbman on 2007-04-23
well, i just did a fresh install.  Of course it's all good now.  Now I just need to spend a few hours reinstalling all the software I had.

---

### Post by xtreme35967 on 2007-04-23
Thats good but it sucks that you had to start over.

---

### Post by Nossie on 2007-06-08
Hey, 

maybe you can help me instead :D

I'm running into the same problems as the thread starter ... and I'm not too happy about killing the OS to try and fix it ...

I ran feisty pre release not too long ago and just before my mobo died I crashed feisty by trying to enable graphics support... I never fixed it due to the board issues and forgot about linux till now... I couldnt get the desktop effects running then and I think I bombed the system trying to install other new nvidia drivers.. (in the past on mandrake (refuse to call it mandriva) I've recompiled the nvidia driver from source due to having a kernel that supported more than 1GB of memory and I've edited the Xconfig to change it from open source to commercial... this time when I crashed X, I didnt revert it back to the nv drivers because a) my mobo died shortly after b) I only really wanted to try out beryl.

The last week or so... I've installed ubuntu, crossover, beryl and some parts of compiz....  wow runs extremely slowly in D3D mode as expected and fails to run at all in openGL... screensavers live a short life before freezing and tuxracer seems abysmally slower than I remember.

In all my linux experience (which I admit isnt that much) going back to redhat 5.2, I've never managed to get GLX drivers working effectively and at the best of times was able to play Americas Army fine on only 2 or so different occasions...

I crashed X again tonight after unsucessfully trying to enable rendering... I assumed it had something to do with GLX and looked it up in synaptic to find
```

To enable the driver, run "sudo nvidia-glx-config enable".
```

I tried doing that, and seemed ok, restarted X and no screens could be found..... fixed by reinstalling the nvidia drivers...

now, although desktop effects were enabled before the crash, they now are not... beryl wasnt working and had reverted back to gnomes own but seemed to automagically fix itself with a few x restarts

I'm pretty lost as to how to get  direct rendering working :(

```
ian@Jupiter-Ubuntu:~$ glxinfo | grep rendering
direct rendering: No
ian@Jupiter-Ubuntu:~$ 
```


```
# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder3)  Thu Nov  9 17:55:20 PST 2006

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
    Identifier     "Generic Monitor"
    HorizSync       28.0 - 51.0
    VertRefresh     43.0 - 60.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Generic Video Card"
    Driver         "nvidia"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "Generic Video Card"
    Monitor        "Generic Monitor"
    DefaultDepth    24
    Option         "AddARGBGLXVisuals" "True"
    SubSection     "Display"
        Depth       1
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1600x1200" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection

Section "Extensions"
    Option         "Composite" "Enable"
EndSection

```

Originally Ubuntu wouldn't detect any resolutions higher than 1024x768, I edited xconf to fix that...

Ubuntu only detects the card as generic but really its a Nvidia 6800 GTS

any help would be greatfuly appreciated, ty for your time.

Ian.

---

### Post by Nossie on 2007-06-09
For anyone that needs to know how I fixed the problem (I hope)

I ran a niffty util from nvidia to get things configured properly then added the lines in bold ...

```
# nvidia-settings: X configuration file generated by nvidia-settings
# nvidia-settings:  version 1.0  (buildmeister@builder3)  Thu Nov  9 17:56:12 PST 2006

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Files"
    RgbPath         "/usr/X11R6/lib/X11/rgb"
EndSection

Section "Module"
    Load           "dbe"
    Load           "extmod"
    Load           "type1"
    Load           "freetype"
    Load           "glx"
EndSection

Section "ServerFlags"
    Option         "Xinerama" "0"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "Monitor"
    # HorizSync source: edid, VertRefresh source: edid
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "HP 2025"
    HorizSync       30.0 - 92.0
    VertRefresh     56.0 - 85.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Videocard0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 6800 GS"
    [b]Option "AddARGBGLXVisuals" "True"
    Option "RenderAccel" "true"
    Option "TripleBuffer" "true"
    Option "AllowGLXWithComposite" "true"[/b]
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "metamodes" "1600x1024 +0+0; 800x600 +0+0; 640x480 +0+0"
    SubSection     "Display"
        Depth       24
        Modes      "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection

```

hope that helps for someone...

the end result ... beryl works wonderfully... my monitor/card is fully identified and course.......

```
ian@Jupiter-ubuntu:~$ glxinfo | grep rendering
direct rendering: Yes
ian@Jupiter-ubuntu:~$ 

```
now...  I hope wow will work :D

---

### Post by bodhi.zazen on 2007-06-09
To configure a nvidia card for Beryl, enter this in a terminal :

```
sudo nvidia-xconfig

 sudo nvidia-xconfig -composite; sudo nvidia-xconfig -allow-glx-with-composite
 sudo nvidia-xconfig -render-accel; sudo nvidia-xconfig -add-argb-glx-visuals
```

The first command configures X AND makes a back up of xorg.conf if needed

The second is all 1 long line, or a series of commands separated by ;

---

### Post by zer0x41 on 2007-06-13
> **xboxbman said:**
> well, i just did a fresh install.  Of course it's all good now.  Now I just need to spend a few hours reinstalling all the software I had.

Hi xboxbman, if you still looking this thread, this is my opinion...

I saw your xorg.conf file and i observe that a part of code is missing.
In terminal press:
```
sudo gedit /etc/X11/xorg.conf
```

Check at the bottom of the text if you have this section:
```

Section "Extensions"
    Option         "Composite" "Enable"
EndSection

```
If you do it's ok, but if you don't try to add it. Save the file and press
"Ctrl+Alt+Backspace" to restart your X server! See if worked and please reply me...

Good Luck! :)

---

