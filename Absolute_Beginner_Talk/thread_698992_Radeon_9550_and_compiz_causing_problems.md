---
title: "Radeon 9550 and compiz causing problems"
date: 2008-02-16
forum: Absolute Beginner Talk
---

### Post by K_Boomer on 2008-02-16
Need help ASAP with graphics card problems. 

System: Ubuntu 7.10
Card: Radeon 9550

I have been working about two or three weeks on the problems my graphics card is creating, and I have tried quite a lot. Note that compiz is working fine and desktop effects are fantastic.

Problems:
-Xscreensaver is extremely sluggish and laggy. 
-Whenever I enter compiz into terminal, i lose the top bar on my windows and computer sometimes restarts.
-Cannot play Half-life 2 (steam opens, but when I launch, nothing happens)
-Computer randomly freezes

I have:
Installed latest radeon 9550 driver using envy.
Reinstalled compiz.
Reinstalled wine and steam
Tried editing parts of xorg.conf "extensions"

Big problem:
When I try to get Half-Life 2 going, sometimes after I press launch my resolution immediately drops to 800x600 and then my computer restarts. I am then stuck in that resolution until i terminal dpkg-reconfigure xserver-xorg and set things right again. It is very annoying


my xorg.conf:

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
	Identifier	"ATI Technologies Inc RV350 AS [Radeon 9550]"
	Driver		"fglrx"
	Busid		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"19''"
	Option		"DPMS"
	Horizsync	24-80
	Vertrefresh	50-75
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies Inc RV350 AS [Radeon 9550]"
	Monitor		"19''"
	Defaultdepth	24
	SubSection "Display"
		Modes		"1280x1024"	"1280x960"	"1152x864"	"1024x768"	"800x600"	"640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen "Default Screen"
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
	
	# Uncomment if you have a wacom tablet
	#	InputDevice     "stylus"	"SendCoreEvents"
	#	InputDevice     "cursor"	"SendCoreEvents"
	#	InputDevice     "eraser"	"SendCoreEvents"
EndSection
Section "Module"
	Load		"glx"
EndSection
Section "Extensions"
	Option		"Composite"	"0"
EndSection


*Note that I have tried changing the "0" in extensions to "enable" and other variants, only to find my computer restarts and will not even get into the login screen. I once again have to dpkg-reconfigure xserver-xorg. It's a pain.


I have tried a lot of things, so please don't post me a generic "How to" link: Chances are I have already read it and it didn't help. I have searched the web and KVirc channels for assistance. NO luck. 

I want to post compiz, but last time, when I was writing this very thread, compiz caused my computer to freeze up and I lost everything I wrote.

---

### Post by K_Boomer on 2008-02-16
compiz
Checking for Xgl: present. 
Checking for nVidia: not present. 
Checking for Xgl: present. 
Enabling Xgl with fglrx ATi drivers...
Starting gtk-window-decorator
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format

yup. after entering compiz into terminal, i lost all top bars to my windows and when i type, each letter lags about 10 seconds. in fact i cannot see the sentence i amtyping now until i wait for about 15 seconds.... i really hate all this trouble.

---

### Post by spiderbatdad on 2008-02-16
that probably isn't the best way to start compiz. I assume you have installed compizconfig-settings-manager. You should also have an emerald theme in place for managing your window borders. The problem also could be in the rendering tool. There is a program available for enabling/disabling compiz, and it simultaneously switches the windows manager and chosen rendering tool. I believe it is called compiz icon. I will try to find a link to it for you. It includes a configuration menu for you compiz choices. It does not interfere with your compiz settings.

---

### Post by K_Boomer on 2008-02-16
ooo. thanks for a post. I would love to check out that link to see if I can tidy this problem up.

---

### Post by spiderbatdad on 2008-02-16
[http://neoaddict.wordpress.com/2007/11/03/getting-fusion-icon/](http://neoaddict.wordpress.com/2007/11/03/getting-fusion-icon/)

This deb for feisty is supposed to work in gutsy as well, and would be easier to install: [http://tombuntu.com/index.php/2007/08/26/compiz-fusion-tray-icon/](http://tombuntu.com/index.php/2007/08/26/compiz-fusion-tray-icon/)

I gave up after beryl because my graphics card wasn't up to par, but I did use this icon before and it worked well. It allows you to change the rendering and windows manager, and keeps your settings.

---

### Post by K_Boomer on 2008-02-16
set up the first link. theni tried runnig the program. now my top menu bars are gone again and i cant see what i tyope again. this is exactly what happens when i ran compiz in terminal....

---

### Post by K_Boomer on 2008-02-17
ok. switched to indirect rendering. that work decent. Found out that if I switch to metacity as window manager, the typing problem occurs. Maybe the problem? I dont know how to solve it though. Thanks for helping me out this far.

---

### Post by K_Boomer on 2008-02-17
can anybody help with the HL2 problem or the xscreensaver problem?

---

