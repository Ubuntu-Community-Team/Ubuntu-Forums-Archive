---
title: "Beryl is driving me crazy!"
date: 2007-07-22
forum: Absolute Beginner Talk
---

### Post by darknightx on 2007-07-22
Hi everybody... I just need help from somebody... this is my problem and is driving me crazy!

I installed Ubuntu Festy Fawn on my PC and everything is super!. The problem is that as soon as I installed Beryl and in the terminal I typed : "beryl" everything crashed and the only thing that continued working was the terminal.
My video card is GeForce4 MX 4000 AGP 8x with 128 MB, so I downloaded the drivers and tried to install them.
After that I tried to reconfigure the Xserver with dpkg-reconfigure... but the only thing that I won was loosing the video mode. 
I have tried to change in some line of the the xorg.conf file the "nv" to "nvidia" but the result was loosing the video...

Also when I type on the terminal "beryl-manager" the result is : 
x@kiev:~$ Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Found not compatible window manager. Waiting...  

After the last line... the computer crashes..


What is supposed to be done? what is Xlib and GLX

Thanks

darknightx

---

### Post by FleetAdmiral74 on 2007-07-22
Very little development on Beryl now...it merged w/ Compiz, what you want is Compiz Fusion. It is more up to date and stable, so...good luck!

---

### Post by wordgf on 2007-07-22
did you installed nvidia-glx drivers?
if not open a terminal and type::


sudo apt-get install nvidia-glx
 
I suggest this links ::
[http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_setup_nvidia_drivers_in_7.04](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_setup_nvidia_drivers_in_7.04)
[http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_Beryl_.28Nvidia.29](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_Beryl_.28Nvidia.29)

and sorry for my english...

:)

---

### Post by Hobo Joe on 2007-07-22
Post the output of:
```

glxinfo

```
That should help us pin down the problem.

---

### Post by marco999 on 2007-07-22
Sound as tho, you installed the non-legacy drivers when you needed the legacy drivers or that your xorg.conf file is not changed to "nvidia" instead of "NV" when u try to run Beryl. Resulting in a crash.

U may want to try Compiz-Fusion it is the latest version or Beryl, since the merging of compiz and beryl.

Marco999

---

### Post by crimesaucer on 2007-07-22
> **FleetAdmiral74 said:**
> Very little development on Beryl now...it merged w/ Compiz, what you want is Compiz Fusion. It is more up to date and stable, so...good luck!

Agreed, might as well get with the current Compiz Fusion, instead of struggling to get a program that is discontinued to work properly.

---

### Post by darknightx on 2007-07-26
Hi! I read all the thread, so I tried to install some libraries. The result is when I type glxinfo:

x@kiev:~$ glxinfo
name of display: :0.0
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x21 24 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x22 24 dc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x5b 32 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
x@kiev:~$ 

So I dont know what to do.  Right now I know that compiz is better than Beryl , but anyway I cant install it. 
Mi Nvidia graphic card is not working... I think that the big point is my lack of experience, but anyway, I just want to learn.
So I guess that you may need more info , so I am going to put the code of the Xorg.conf , to let you have an idea of what I have.



# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
	FontPath	"/usr/share/fonts/X11/misc"
	FontPath	"/usr/share/fonts/X11/cyrillic"
	FontPath	"/usr/share/fonts/X11/100dpi/:unscaled"
	FontPath	"/usr/share/fonts/X11/75dpi/:unscaled"
	FontPath	"/usr/share/fonts/X11/Type1"
	FontPath	"/usr/share/fonts/X11/100dpi"
	FontPath	"/usr/share/fonts/X11/75dpi"
	# path to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load	"i2c"
	Load	"bitmap"
	Load	"ddc"
	#Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"latam"
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
	Identifier	"nVidia Corporation NV18 [GeForce4 MX 4000]"
	Driver		"nvidia"
	Option          "RenderAccel" "true"
         Option         "AllowGLXWithComposite" "true"

	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"7E"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"nVidia Corporation NV18 [GeForce4 MX 4000]"
	Monitor		"7E"
	DefaultDepth	 24
	SubSection "Display"
		Depth		1
		Modes		"1336x1336" "1027x768" "1024x768" "800x600" "640x480" "272x272" "248x248" "248x198"
	EndSubSection
	Option         "AddARGBGLXVisuals" "true"
	Option         "DisableGLXRootClipping" "true"
	SubSection "Display"
		Depth		4
		Modes		"1336x1336" "1027x768" "1024x768" "800x600" "640x480" "272x272" "248x248" "248x198"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1336x1336" "1027x768" "1024x768" "800x600" "640x480" "272x272" "248x248" "248x198"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1336x1336" "1027x768" "1024x768" "800x600" "640x480" "272x272" "248x248" "248x198"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1336x1336" "1027x768" "1024x768" "800x600" "640x480" "272x272" "248x248" "248x198"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1336x1336" "1027x768" "1024x768" "800x600" "640x480" "272x272" "248x248" "248x198"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus"	"SendCoreEvents"
	InputDevice     "cursor"	"SendCoreEvents"
	InputDevice     "eraser"	"SendCoreEvents"
EndSection

Section "DRI"
	Mode	0666
EndSection

---

