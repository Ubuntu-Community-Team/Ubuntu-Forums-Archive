---
title: "why my 3dgraphics runs so slowly on ubuntu ???"
date: 2006-06-24
forum: Absolute Beginner Talk
---

### Post by MaximB on 2006-06-24
I've installed my 3dgraphic card - ATI 9800 pro
I used the command like first - it did installed the ati card but it was very slow
I've found adriver for linux at [www.ati.com](www.ati.com) - support
and I got the same results

all even the very small 3dgames/screensavers run very slowly and completly unplayable
in winxp hoever it runs PERFECT.
why ? does it suposed to run that slowly on ubuntu 6.06 ?

maybe I did somthing wrong and didn't installed it correctly ?
there are TONS of guilds to how to install ATI graphic cards I can't try them all...
there must be an easy way to install it...
can someone of pose a GUI installation plz...?

---

### Post by FredB on 2006-06-24
ATi are known to be hard to install under ubuntu and linux in general.

[https://wiki.ubuntu.com/RadeonDriverHowto?highlight=%28Radeon%29](https://wiki.ubuntu.com/RadeonDriverHowto?highlight=%28Radeon%29)

Good luck.

---

### Post by MaximB on 2006-06-24
the wiki you posted : [https://wiki.ubuntu.com/RadeonDriverHowto?highlight=%28Radeon%29](https://wiki.ubuntu.com/RadeonDriverHowto?highlight=%28Radeon%29)
says that my graphic card :
"Radeon 9800PRO/9800SE/9800, FireGL X2 (2D only)"
what do they mean by "2d only" ?
won't it be capable of running 3dgames good and fast under ubuntu 6.06 ?

---

### Post by MaximB on 2006-06-24
sorry , I had to pose replay to myself - i'm already ae the fifth page...
what is it about 2d only ? (read above)

---

### Post by FredB on 2006-06-25
[QUOTE=MAXDDARK]sorry , I had to pose replay to myself - i'm already ae the fifth page...
what is it about 2d only ? (read above)[/QUOTE]

I'm afraid you got your answer in your previous post. ATI are really hard to setup on linux. So I am afraid under linux with this card, you will not have any 3D acceleration available :(

---

### Post by MaximB on 2006-06-25
when it would be possible to use my 3dcard on ubuntu ?
is there a chance that it would be fixed in the few next updates for ubuntu ?
cuz in this case I will never delete my winxp partition...

---

### Post by mcduck on 2006-06-25
It's not the radeon driver you want, but the Ati's proprietary driver, fglrx. If you're using Dapper, it's available in Ubuntu repositories for easy install:

[SIZE="4"]**Install instructions for Ubuntu 6.06 (Dapper Drake)**[/SIZE]

```
sudo apt-get update 
sudo apt-get install linux-restricted-modules-$(uname -r)
sudo apt-get install xorg-driver-fglrx
sudo aticonfig --initial
sudo aticonfig --overlay-type=Xv

```
Then you need to manually edit the xorg.conf file. So:

```
sudo gedit /etc/X11/xorg.conf
```

Under Section "Screen" The Identifier line needs to be changed to:

     Identifier "aticonfig-Screen[0]"

Reboot.

Confirm it worked:

```
$ fglrxinfo 
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9700 Generic
OpenGL version string: 2.0.5755 (8.24.8)
```

Source: [http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide]("http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide")

If you receive a message Xlib:  extension "XFree86-DRI" missing on display ":1.0, edit your /etc/X11/xorg.conf and add the line load "dri" in Section "Module"

---

### Post by MaximB on 2006-06-25
MCDUCK - I've done everything you wrote and it completly screw up my GUI - system !!!
I tried to put it to the previeus condition - but it did not help
so I'm writing from my XP
insted ubuntu beaing my "recovery" OS ...winxp comes to be...

here are my errors :

failed to start x server
undefind screen "deault screen"
(EE) problem parsing the config file
(EE) error parsing the config file
fatal server error
no screens found
(WW) KDSET MODE failed bad file descripter
VT GETMODE failed bad file descripter

I can't use the gedit command , I can only edit this file from winxp
what am I to do from now ???

---

### Post by MaximB on 2006-06-25
sorry but I URGENTLY need your help

---

### Post by raptros-v76 on 2006-06-25
post your xorg.conf

---

### Post by MaximB on 2006-06-25
my currebt and modified xorg.conf :


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
	Load  "bitmap"
	Load  "dbe"
	Load  "ddc"
	Load  "dri"
	Load  "extmod"
	Load  "freetype"
	Load  "glx"
	Load  "int10"
	Load  "record"
	Load  "type1"
	Load  "v4l"
	Load  "vbe"
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
	Option	    "CorePointer"
	Option	    "Device" "/dev/input/mice"
	Option	    "Protocol" "ExplorerPS/2"
	Option	    "ZAxisMapping" "4 5"
	Option	    "Emulate3Buttons" "true"
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
	Identifier  "stylus"
	Driver      "wacom"
	Option	    "Device" "/dev/wacom"          # Change to 
	Option	    "Type" "stylus"
	Option	    "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
	Identifier  "eraser"
	Driver      "wacom"
	Option	    "Device" "/dev/wacom"          # Change to 
	Option	    "Type" "eraser"
	Option	    "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
	Identifier  "cursor"
	Driver      "wacom"
	Option	    "Device" "/dev/wacom"          # Change to 
	Option	    "Type" "cursor"
	Option	    "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "Monitor"
	Identifier   "Generic Monitor"
	HorizSync    30.0 - 60.0
	VertRefresh  50.0 - 75.0
	Option	    "DPMS"
EndSection

Section "Device"
	Identifier  "ATI Technologies, Inc. Radeon R350 NH [Radeon 9800 Pro]"
	Driver      "fglrx"
	VideoRam    256000
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
	Option	    "UseInternalAGPGART" "no"
	BusID       "PCI:1:0:0"
EndSection

Section "Screen"
	Identifier "aticonfig-screen[0]"
	Device     "ATI Technologies, Inc. Radeon R350 NH [Radeon 9800 Pro]"
	Monitor    "Generic Monitor"
	DefaultDepth     24
	SubSection "Display"
		Depth     1
		Modes    "1920x1440" "1920x1200" "1856x1392" "1792x1344" "1680x1050" "1600x1200" "1440x900" "1400x1050" "1280x1024" "1280x960" "1280x854" "1280x800" "1280x768" "1200x800" "1152x864" "1152x768" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     4
		Modes    "1920x1440" "1920x1200" "1856x1392" "1792x1344" "1680x1050" "1600x1200" "1440x900" "1400x1050" "1280x1024" "1280x960" "1280x854" "1280x800" "1280x768" "1200x800" "1152x864" "1152x768" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     8
		Modes    "1920x1440" "1920x1200" "1856x1392" "1792x1344" "1680x1050" "1600x1200" "1440x900" "1400x1050" "1280x1024" "1280x960" "1280x854" "1280x800" "1280x768" "1200x800" "1152x864" "1152x768" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     15
		Modes    "1920x1440" "1920x1200" "1856x1392" "1792x1344" "1680x1050" "1600x1200" "1440x900" "1400x1050" "1280x1024" "1280x960" "1280x854" "1280x800" "1280x768" "1200x800" "1152x864" "1152x768" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     16
		Modes    "1920x1440" "1920x1200" "1856x1392" "1792x1344" "1680x1050" "1600x1200" "1440x900" "1400x1050" "1280x1024" "1280x960" "1280x854" "1280x800" "1280x768" "1200x800" "1152x864" "1152x768" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     24
		Modes    "1920x1440" "1920x1200" "1856x1392" "1792x1344" "1680x1050" "1600x1200" "1440x900" "1400x1050" "1280x1024" "1280x960" "1280x854" "1280x800" "1280x768" "1200x800" "1152x864" "1152x768" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "DRI"
	Mode         0666
EndSection

---

### Post by raptros-v76 on 2006-06-25
change the top part of it.
```

 Section "ServerLayout"
 Identifier "Default Layout"
 **Screen "aticonfig-screen[0]" 0 0** #this line needs to be changed
 InputDevice "Generic Keyboard"
 InputDevice "Configured Mouse"
 InputDevice "stylus" "SendCoreEvents"
 InputDevice "cursor" "SendCoreEvents"
 InputDevice "eraser" "SendCoreEvents"
 EndSection

```

---

### Post by MaximB on 2006-06-25
Screen "aticonfig-screen[0]" 0 0 #this line needs to be changed
to what ?
what should I change it to ? (write the full new line plz...)

---

### Post by raptros-v76 on 2006-06-25
that is the new line.

---

### Post by raptros-v76 on 2006-06-25
ok look at the serverlayout section. currently, yours is this:

```

Section "ServerLayout"
 Identifier "Default Layout"
 Screen "Default Screen" 0 0
 InputDevice "Generic Keyboard"
 InputDevice "Configured Mouse"
 InputDevice "stylus" "SendCoreEvents"
 InputDevice "cursor" "SendCoreEvents"
 InputDevice "eraser" "SendCoreEvents"
 EndSection

```

it needs to be changed to:
```

Section "ServerLayout"
 Identifier "Default Layout"
** Screen "aticonfig-screen[0]" 0 0**
 InputDevice "Generic Keyboard"
 InputDevice "Configured Mouse"
 InputDevice "stylus" "SendCoreEvents"
 InputDevice "cursor" "SendCoreEvents"
 InputDevice "eraser" "SendCoreEvents"
 EndSection

```

---

### Post by MaximB on 2006-06-25
say hello to my new ubuntu 6.06 with ati support !!!
thank all of you , you just saved my day !!!
mcduck - you just forgot to say that I have to change the same line in the "serverLayout".

BUT THNX...
I am very greatfull.

---

### Post by raptros-v76 on 2006-06-25
have fun with good graphics now. and ask for help if you need it.

---

### Post by MaximB on 2006-06-25
and now....
are there a good 3dfree/open source games out there ???
:)

---

### Post by jimrz on 2006-06-25
[QUOTE=MAXDDARK]MCDUCK - I've done everything you wrote and it completly screw up my GUI - system !!!
I tried to put it to the previeus condition - but it did not help
so I'm writing from my XP
insted ubuntu beaing my "recovery" OS ...winxp comes to be...

here are my errors :

failed to start x server
undefind screen [COLOR="Red"]**"deault screen"**[/COLOR]
(EE) problem parsing the config file
(EE) error parsing the config file
fatal server error
no screens found
(WW) KDSET MODE failed bad file descripter
VT GETMODE failed bad file descripter

I can't use the gedit command , I can only edit this file from winxp
what am I to do from now ???[/QUOTE]

think the highlighted above should read "default screen"

---

### Post by MaximB on 2006-06-25
the "F" just gone wild !!!   :)
that I wrote by hand - not copy/paste...

---

