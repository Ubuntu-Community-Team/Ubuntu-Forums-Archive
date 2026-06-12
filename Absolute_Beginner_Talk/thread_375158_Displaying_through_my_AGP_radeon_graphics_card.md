---
title: "Displaying through my AGP radeon graphics card?"
date: 2007-03-03
forum: Absolute Beginner Talk
---

### Post by Neon_Knight on 2007-03-03
Right, I've asked about this at [www.linuxquestions.org](www.linuxquestions.org) , but I don't understand most of what the people are suggesting I do about this problem. 

[http://www.linuxquestions.org/questions/showthread.php?t=528994&highlight=the_neon_knight%23](http://www.linuxquestions.org/questions/showthread.php?t=528994&highlight=the_neon_knight%23)

There's the original thread, if you want to read it, but I'll explain it here anyway.

I can't get Ubuntu to display through my AGP radeon 9550 graphics card. It complains about X not being set up correctly and I have to do something with xorg.conf but I'm not sure what or how...

It displays through my onboard fine (after I took out my gfx card), but when I try to boot through the AGP card, it comes up with the message and then goes into command line mode. 

Any ideas, guys? Thanks in advance.

---

### Post by angryfirelord on 2007-03-03
What I think is happening is that Ubuntu isn't seeing your other video card. Instead, it first sees the onboard Intel video card and tries to read that. Therefore, when you try to load Ubuntu through a different card, it doesn't know what to do.

Consult your manual & disable the onboard video, which is located in your BIOS. The instructions vary per motherboard manufacturer.

Now, if that still doesn't work, go to the part called Section "Device" under your xorg.conf file. Change the driver to read "vesa". Reboot.

---

### Post by Neon_Knight on 2007-03-03
> **angryfirelord said:**
> What I think is happening is that Ubuntu isn't seeing your other video card. Instead, it first sees the onboard Intel video card and tries to read that. Therefore, when you try to load Ubuntu through a different card, it doesn't know what to do.

Consult your manual & disable the onboard video, which is located in your BIOS. The instructions vary per motherboard manufacturer.

Now, if that still doesn't work, go to the part called Section "Device" under your xorg.conf file. Change the driver to read "vesa". Reboot.

Well, Windows XP can detect my Radeon just fine.. And my motherboard BIOS does not have an option to disable the onboard. If there's a graphics card plugged in, it'll use it. I actually physically can't disable the onboard, unless I take a sledgehammer to it. If Ubuntu couldn't SEE the video card, how does it display the command line and the startup loading screens through it? 

And it already does read "vesa" on the xorg.conf file.

---

### Post by freebird54 on 2007-03-03
I am running a 9550 Radeon here on Ubuntu, so that is not the source of the problem.  Could you post your xorg.conf file?  I suspect that you need to specify which screen X windows is trying to run on...

It should have seen both cards, but perhaps it auto-configured X to use the onboard video as a default.

BTW - I have had much more trouble with the video drivers for this card on XP Pro.. it keeps losing them, and then not starting them when they are replaced again.  (love that registry system, NOT)

---

### Post by Neon_Knight on 2007-03-03
I thought it was something to do with changing the xorg.conf file to specify the AGP slot, instead of the onboard, which I have no idea how to do. :) 

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
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"gb"
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
	Identifier	"Intel Corporation 82865G Integrated Graphics Controller"
	Driver		"vesa"
	BusID		"PCI:0:2:0"
EndSection

Section "Monitor"
	Identifier	"CY-465"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation 82865G Integrated Graphics Controller"
	Monitor		"CY-465"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1024x768" "832x624" "800x600" "720x400" "640x480"
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

That's my xorg.conf.

:lolflag:

---

### Post by freebird54 on 2007-03-03
OK - we found the problem - now all we need is the solution!  Hopefully this is one...

First - back that xorg.conf file up

> sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup

then we try to configure X with the AGP card in control..

> sudo dpkg-reconfigure xserver-xorg

It will have you answer a lot of unrelated questions - for which the defaults will mostly do fine (it explains them quite well).  Choose the vesa driver for now.  Make sure you select appropriate resolutions for your display.  After this is completed try to

> startx

and hopefuily all will be usable!

THEN you can later add the fglrx driver for better results/3d acceleration etc etc by following any number of HOW_TOs/Threads around here... (or ask again - I might be able to find it all again!)

Good fortune... :)

---

### Post by Neon_Knight on 2007-03-03
Oooo I'm getting excited now! This has been a problem for me for around 6 months and now it's finally seeing the light! THE LIGHT!!!!

Right, what's the bus ID for AGP?

PCI:x:y:z 

It has it set to defaultly PCI:0:2:0 but I presume that would be my onboard Intel graphics, because that's the only graphics it's ever been told to use...


Also, take note: I don't actually have my AGP radeon card plugged in. Because if I have it plugged in, then the BIOs will display through it and give me my beloved error message. I hope that won't be a problem...

---

### Post by Neon_Knight on 2007-03-03
I hate to bump, but I'm kinda...aching for a response here...

---

### Post by Neon_Knight on 2007-03-03
Okay, well I tried it anyway, using PCI:1:0:1 (I read somewhere on google that it would work) and it didn't work. Same problem, but this time it didn't boot with the onboard either.

It was a pain trying to find my way through the command line to rename the backup and things....

well anyway, what do you think now? Was PCI:1:0:1 wrong? which questions on that thing are actually relevant?

And it never actually asked me about vesa (or any other) drivers....

---

### Post by angryfirelord on 2007-03-03
Try PCI:1:0:0. That's what mine is set to.

It asks about the drivers on the very first page.

---

### Post by Neon_Knight on 2007-03-03
HOSHI-

IT ACTUALLY WORKED!!!!

Man, that's awesome.

Do you know how I can now get my resoultion higher?

---

### Post by angryfirelord on 2007-03-03
> **Neon_Knight said:**
> HOSHI-

IT ACTUALLY WORKED!!!!

Man, that's awesome.

Do you know how I can now get my resoultion higher?

lol that's good.

Resolutions can also be configured using the **sudo dpkg-reconfigure xserver-xorg** command. I believe that the resolution choices are on the second to last page of the setup. Be careful that you don't set a resolution that too high as I believe that there is no safeguard against that. (I just have it set to 1024x768, but most monitors can handle 1280x1024, depending on the size and model).

Or, you could go to your xorg.conf file and input them manually.

---

### Post by freebird54 on 2007-03-04
Have you tried my 'fix' yet?  The idea is to type those commands in AFTER it fails to start the graphics system, and gives you all those complaints.  If the card IN USE is the AGP one, that should be the one configured/identified and set up by the dpkg-reconfigure command.

BTW - that command will give you a text mode interface for setting up nearly everything in X windows - your mouse, keyboard, monitor (including resolution choices) and will automagically detect the card and PCI interface to direct itself to.  Navigate with arrow keys, <SPACE> to select (within a list)  and the <TAB> key to get to <OK>, and <ENTER> to move on/confirm your choices.  Remember to choose the vesa driver for now - it is slow but seems reliable - and you can get into getting game ready after you can see what you're doing.

If it's too much detail, sorry - if it's not enough just say so!

Let me know, please, how it goes (post here is fine)

---

