---
title: "debian4.0 changing resolution"
date: 2007-07-29
forum: Absolute Beginner Talk
---

### Post by dynoweb on 2007-07-29
I just installed debian4.0 and I can not find how to change the resolution.
I was using ubuntu6.10 and I want to see how Debian4.0 works.
I only have one resolution to choose from and my desktop is really choppy.
How do i get the correct resolution ( 1024x768 )?

current resolution is 640x480

---

### Post by r4ik on 2007-07-29
This could be usefull,

[http://code.google.com/p/hakix/](http://code.google.com/p/hakix/)

Good luck !

---

### Post by dynoweb on 2007-07-29
> **r4ik said:**
> This could be usefull,

[http://code.google.com/p/hakix/](http://code.google.com/p/hakix/)

Good luck !

not all the dependencies are in the package

---

### Post by kerry_s on 2007-07-29
just edit your /etc/X11/xorg.conf

su
xedit /etc/X11/xorg.conf

```
Section "Screen"                                                                
        Identifier      "Default Screen"                                        
        Device          "Generic Video Card"                                    
        Monitor         "Generic Monitor"                                       
        DefaultDepth    24                                                      
        SubSection "Display"                                                    
                Depth           24                                              
                Modes           "1024x768"                                      
        EndSubSection                                                           
EndSection 
```

press save 2 times and logout,then ctrl+alt+backspace to restart X
make sure you install "mc"(su apt-get install mc) it can save you a lot of typing if you get stuck at command line, just type mc or su mc depending what you need to change.

---

### Post by dynoweb on 2007-07-29
> **kerry_s said:**
> just edit your /etc/X11/xorg.conf

su
xedit /etc/X11/xorg.conf

```
Section "Screen"                                                                
        Identifier      "Default Screen"                                        
        Device          "Generic Video Card"                                    
        Monitor         "Generic Monitor"                                       
        DefaultDepth    24                                                      
        SubSection "Display"                                                    
                Depth           24                                              
                Modes           "1024x768"                                      
        EndSubSection                                                           
EndSection 
```

press save 2 times and logout,then ctrl+alt+backspace to restart X
make sure you install "mc"(su apt-get install mc) it can save you a lot of typing if you get stuck at command line, just type mc or su mc depending what you need to change.




none of this stuff is working anything else?

---

### Post by r4ik on 2007-07-29
Have you got GDebi installed ?

---

### Post by dynoweb on 2007-07-29
> **r4ik said:**
> Have you got GDebi installed ?

yes i do

---

### Post by r4ik on 2007-07-29
Please read,

[http://www.debian-multimedia.org/](http://www.debian-multimedia.org/)

But do scroll down a bit.

---

### Post by r4ik on 2007-07-29
Forget above post install the missing it should be in Synaptic.

---

### Post by dynoweb on 2007-07-29
> **r4ik said:**
> Forget above post install the missing it should be in Synaptic.

not in synaptic

I just want to change my screen resolution... hoiw hard does this have to be?
I am using Debian4.0

---

### Post by dynoweb on 2007-07-29
does anyone know how to change resolution to 1024x768

---

### Post by kerry_s on 2007-07-29
do you even got the driver setup for your video card, debian always has it set on "vesa".
 did you run what it says on the top of xorg.conf ( su & dpkg-reconfigure -phigh xserver-xorg )?

if you want detailed instructions, you need to provide detailed specs on your vid. you also need to copy and paste your xorg.conf here so we can see it and make the changes you need for your card, were not psychics here. we can only go with what you tell us.

---

### Post by dynoweb on 2007-07-30
> **kerry_s said:**
> do you even got the driver setup for your video card, debian always has it set on "vesa".
 did you run what it says on the top of xorg.conf ( su & dpkg-reconfigure -phigh xserver-xorg )?

if you want detailed instructions, you need to provide detailed specs on your vid. you also need to copy and paste your xorg.conf here so we can see it and make the changes you need for your card, were not psychics here. we can only go with what you tell us.

So how do i access that file? I have 3 or 4 different terminals.
root terminal
teminal
x-terminal as root (GKsu)
gnome terminal

I dont know which one to use because they do not open that file that EVERYONE is saying to open... so it does me no good to tell me to open it if i can not open it.

I do not knmow how to change the driver or install the driver to set my video card.
Please tell me how.

Thank you

---

### Post by dynoweb on 2007-07-30
> **dynoweb said:**
> So how do i access that file? I have 3 or 4 different terminals.
root terminal
teminal
x-terminal as root (GKsu)
gnome terminal

I dont know which one to use because they do not open that file that EVERYONE is saying to open... so it does me no good to tell me to open it if i can not open it.

I do not knmow how to change the driver or install the driver to set my video card.
Please tell me how.

Thank you

```

# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the /etc/X11/xorg.conf manual page.
# (Type "man /etc/X11/xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
	FontPath	"/usr/share/fonts/X11/misc"
	FontPath	"/usr/X11R6/lib/X11/fonts/misc"
	FontPath	"/usr/share/fonts/X11/cyrillic"
	FontPath	"/usr/X11R6/lib/X11/fonts/cyrillic"
	FontPath	"/usr/share/fonts/X11/100dpi/:unscaled"
	FontPath	"/usr/X11R6/lib/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/share/fonts/X11/75dpi/:unscaled"
	FontPath	"/usr/X11R6/lib/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/share/fonts/X11/Type1"
	FontPath	"/usr/X11R6/lib/X11/fonts/Type1"
	FontPath	"/usr/share/fonts/X11/100dpi"
	FontPath	"/usr/X11R6/lib/X11/fonts/100dpi"
	FontPath	"/usr/share/fonts/X11/75dpi"
	FontPath	"/usr/X11R6/lib/X11/fonts/75dpi"
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
	Option		"Protocol"		"ImPS/2"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizScrollDelta"	"0"
EndSection

Section "Device"
	Identifier	"ATI Technologies Inc Rage Mobility M3 AGP 2x"
	Driver		"ati"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies Inc Rage Mobility M3 AGP 2x"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1024x768"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice	"Synaptics Touchpad"
EndSection

Section "DRI"
	Mode	0666
EndSection
```

---

