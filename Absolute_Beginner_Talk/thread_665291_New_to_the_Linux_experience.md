---
title: "New to the Linux experience"
date: 2008-01-12
forum: Absolute Beginner Talk
---

### Post by Fox429 on 2008-01-12
Since Im really new to linux, i wasnt sure if I should put my problem here or in another forum, but here it goes. I tried to install the nvidia drivers for my 7300 GT and i get this error code 
```
Error: your X configuration has been altered.
This script cannot proceed automatically. If you believe that this
not correct, you can update the md5sum entry executing the following
command:
md5sum /etc/X11/xorg.conf | sudo tee /var/lib/x11/xorg.conf.md5sum
otherwise edit manually /etc/X11/xorg.conf to change the Driver section
from nv to nvidia.

```
When I type in
```
 sudo nvidia-glx-config enable
```
I have no idea what that error message means or how to fix it. If anyone has some suggestions on how to help, they will be greatly appreciated!

p.s. i used the Synaptic thing to install the packages and it was the nvidia-glx package. Im also on the 6.06 version of Ubuntu.

---

### Post by dcstar on 2008-01-12
> **Fox429 said:**
> Since Im really new to linux, i wasnt sure if I should put my problem here or in another forum, but here it goes. I tried to install the nvidia drivers for my 7300 GT and i get this error code 
```
Error: your X configuration has been altered.
This script cannot proceed automatically. If you believe that this
not correct, you can update the md5sum entry executing the following
command:
md5sum /etc/X11/xorg.conf | sudo tee /var/lib/x11/xorg.conf.md5sum
otherwise edit manually /etc/X11/xorg.conf to change the Driver section
from nv to nvidia.

```
When I type in
```
 sudo nvidia-glx-config enable
```
I have no idea what that error message means or how to fix it. If anyone has some suggestions on how to help, they will be greatly appreciated!

p.s. i used the Synaptic thing to install the packages and it was the nvidia-glx package. Im also on the 6.06 version of Ubuntu.
In a terminal:
```
gksudo gedit /etc/X11/xorg.conf
```
and manually change the "nv" to "nvidia", then:
```
sudo /etc/init.d/gdm restart
```
and you will soon see if the driver is installed correctly.

---

### Post by Malta paul on 2008-01-12
Hi, If you are using Ubuntu you can install the latest driver for your video card by using 'Envy'
System>Administration>Synapic package manager, then search for Envy.
Good luck:)

---

### Post by Fox429 on 2008-01-12
Thanks guys, but when I try the first way that dcstar said I get

```
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
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ExplorerPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "stylus"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "stylus"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "eraser"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "eraser"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "cursor"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "cursor"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"NVIDIA Corporation NVIDIA Default Card"
	Driver		"vesa"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-51
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NVIDIA Default Card"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus" "SendCoreEvents"
	InputDevice     "cursor" "SendCoreEvents"
	InputDevice     "eraser" "SendCoreEvents"
EndSection

Section "DRI"
	Mode	0666
EndSection
```

and no 'nv' comes up, just NVIDIA Default Card.

As for the version with the Synaptic Package Manager, I searched for Envy, but nothing came up.

---

### Post by eapache on 2008-01-12
For some reason, the nv driver failed so it dropped back to vesa (emergency graphics). Try changing the vesa to nvidia.

---

### Post by Fox429 on 2008-01-12
I tried it and it took away the GUI and left me with a black screen that told me to put in my uname and password. I have no idea if it was supposed to do that or not.

---

### Post by eapache on 2008-01-12
Did you try rebooting? If you reboot and get that again, then log in with your normal username and password, and type```
sudo nano /etc/X11/xorg.conf
```change it back to vesa, Ctrl-O to save, Ctrl-X to exit, then type```
startx
```

---

### Post by Fox429 on 2008-01-12
I did reboot, but It loaded up Ubuntu normally, but this time it flashed an Nvidia splash screen every quickly before showing the login screen. I also went and checked my xorg.conf and it show nvidia still there.
```
Section "Device"
	Identifier	"NVIDIA Corporation NVIDIA Default Card"
	Driver		"nvidia"
	BusID		"PCI:1:0:0"
```

But, if that means the drivers installed, why wont it let me change me resolution to 1440x900? It wont let me go any higher than 1024x768.

---

### Post by eapache on 2008-01-12
It has detected a 'default' monitor, which uses only safe resolutions. Open System>Administration>Screens and Graphics and change your monitor to the correct brand and model.

If you cannot find the right model, go see if you can find your monitor manual. Somewhere in it should be a Horizontal Refresh Rate and a Vertical Sync Rate. Print those out here. Try googling it if you have no manual.

---

### Post by Fox429 on 2008-01-12
Aw man, firstly, Screens and Graphics doesnt show up in my Administration menu... and I tried googling my manual and found it. I have a Westinghouse L1975NW, with that said I could not find the to rates you requested, that is unless you want the Horizontal and Vertical Frequencies. :[

---

### Post by eapache on 2008-01-12
Horizontal and vertival frequencies might be it. Are they in the form of ab-cd? If so, that's what you want.

Open up a terminal (Applications>Accessories) and type in the sudo nano command again. Scroll down to Section:Monitor and change the vertrefresh and horizsync values to what you want. Then scroll down to Section:Screen and under Display Depth "24" add the resolution you want.

Then save, exit, and log out. You don't have to do a full reboot.

Please write down the original values for horizsync and vertrefresh so that if it fails you can fix it.

---

### Post by Fox429 on 2008-01-12
They arent in ab-cd format, its just in kHz and Hz, theyre also only two numbers and I found them in the monitors OSD menu.

I didnt change them because im not sure what they are, but i did change the resolution to the one I want, but its still at the same res.

---

### Post by eapache on 2008-01-12
As an example of what format they are in, they could say:
60-80
120-150

Yours currently say:
28-51
43-60

They vary quite a bit, but as long as each one is a range and not a number, you should try them.

EDIT: if that doesn't work, try the stuff at the bottom here: [http://www.justjournal.com/users/laffer1/2007/06/02](http://www.justjournal.com/users/laffer1/2007/06/02)

---

### Post by Shazaam on 2008-01-12
This is my working Dapper xorg.conf with the nvidia driver. The only difference is the monitor. I have a Viewsonic A90. I also don't load dri and I can play 3d games fine.

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
    FontPath        "/usr/share/X11/fonts/misc"
    FontPath        "/usr/share/X11/fonts/cyrillic"
    FontPath        "/usr/share/X11/fonts/100dpi/:unscaled"
    FontPath        "/usr/share/X11/fonts/75dpi/:unscaled"
    FontPath        "/usr/share/X11/fonts/Type1"
    FontPath        "/usr/share/X11/fonts/100dpi"
    FontPath        "/usr/share/X11/fonts/75dpi"
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
    Load           "type1"
    Load           "vbe"
EndSection

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "CoreKeyboard"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc104"
    Option         "XkbLayout" "us"
EndSection

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ExplorerPS/2"
    Option         "ZAxisMapping" "4 5"
    Option         "Emulate3Buttons" "true"
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
    Identifier     "stylus"
    Driver         "wacom"
    Option         "Device" "/dev/wacom"          # Change to 
    Option         "Type" "stylus"
    Option         "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
    Identifier     "eraser"
    Driver         "wacom"
    Option         "Device" "/dev/wacom"          # Change to 
    Option         "Type" "eraser"
    Option         "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
    Identifier     "cursor"
    Driver         "wacom"
    Option         "Device" "/dev/wacom"          # Change to 
    Option         "Type" "cursor"
    Option         "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "Monitor"
    Identifier     "A90"
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "NVIDIA Corporation NVIDIA Default Card"
    Driver         "nvidia"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "NVIDIA Corporation NVIDIA Default Card"
    Monitor        "A90"
    DefaultDepth    24
    SubSection     "Display"
        Depth       1
        Modes      "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
EndSection

---

### Post by Fox429 on 2008-01-13
Thanks for your help guys, but I tried to edit the xorg.conf. Then tried to reboot but it wouldnt detect my display after that... so I think Ill just deal with the ugly resolution and lurk moar until I understand more about the coding and stuff.

---

