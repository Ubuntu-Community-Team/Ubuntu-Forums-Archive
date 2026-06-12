---
title: "Resolution Problem Docked Laptop - Dell FP2001 monitor"
date: 2006-04-24
forum: Absolute Beginner Talk
---

### Post by mybootorg on 2006-04-24
Hey folks,

I thought I had anhilated every single problem with Ubuntu post-installation this weekend and was all ready to start enjoying it :)  when I docked at work and ran headlong into another one.

In brief: I'm running Ubuntu 5.10 on a Dell Latitude D610 with a ATI Technologies, Inc. Radeon Mobility M300 (M22) Video Card. I docked into a normal Dell Docking Station hooked up to a Dell 21 Flat Panel (FP2001).  I've included the relevant piece of my xorg.conf at the bottom of the post.

At first it would boot up to the point where it initialized Xserver and then drop the video signal.  I fixed this by installing the "fglrx" driver.  However, the best resolution I can get is 1024x768 which is the max of the laptop LCD, but needless to say, the monitor is capable of up to 1600x1200.

I've tried editing my xorg.conf and adding a 1600x1200 mode.  But the result after restart is I have a huge screen that I have to "scroll around" to see the entire desktop.  I've also tried the wizard to reconfigure Xserver and output a new xorg.conf file but that hasn't worked for me either.

I've seen all kinds of advice in various places on how to configure screen resolution for the Dell D610 Laptop however, none of the tutorials seem to fit my video card and some suggest doing things like patching video bios which I'm a little apprensive to do until I've had the opportunity to run this past you pros.

Any suggestions?

Best regards,

Craig Mitchell, St. Louis MO

part of my xorg.conf

Section "Device"
	Identifier	"ATI Technologies, Inc. Radeon Mobility M300 (M22)"
	Driver		"fglrx"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"Laptop LCD"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies, Inc. Radeon Mobility M300 (M22)"
	Monitor		"Laptop LCD"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1024x768
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

---

### Post by IeU on 2006-04-24
i have also a problem like this . . .

i am running ubuntu 6.06 beta livecd . . .

i have a 7800GT and i know mz monitor is capable to reach 1280 x 1024 . . .

but i can only see options to change my resolution until 1024 x 768 . . .

what am i supposed to do, to reach 1280 x 1024 . . . _

thanks

---

### Post by mybootorg on 2006-04-24
Ok, I solved my own problem.  I guess I shouldnt be in the "Absolute Beginner" forum anymore.  :mrgreen:  I'm just afraid of getting klondiked by the pros on the other forums.

Here's what I eventuall ended up with in my xorg.conf:

```
Section "Files"
	FontPath	"/usr/share/X11/fonts/misc"
	FontPath	"/usr/share/X11/fonts/cyrillic"
	FontPath	"/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/Type1"
	FontPath	"/usr/share/X11/fonts/CID"
	FontPath	"/usr/share/X11/fonts/100dpi"
	FontPath	"/usr/share/X11/fonts/75dpi"
        # paths to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
EndSection

Section "Module"
	Load	"GLcore"
	Load	"bitmap"
	Load	"ddc"
	Load	"dri"
# Load "extmod" but omit DGA extension - this must be included as is if you want to change resolution on the fly
  	SubSection "extmod"
    	    Option "omit xfree86-dga"
  	EndSubSection
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
	Option		"Protocol"		"ImPS/2"
	Option		"Emulate3Buttons"	"true"
	Option		"ZAxisMapping"		"4 5"
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
	Identifier	"ATI Technologies, Inc. Radeon Mobility M300 (M22)"
	Driver		"fglrx"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"Dell 2001FPS"
	Option		"DPMS"
	HorizSync	31-81
	VertRefresh	60

EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies, Inc. Radeon Mobility M300 (M22)"
	Monitor		"Dell 2001FPS"
	DefaultDepth	24
	SubSection "Display"
		Depth		24
		Modes		"1600x1200" "1024x768"
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

[SIZE="5"]**Now IeU: **[/SIZE]I don't know what kind of video card you have.  But you're just going to have to do some googling around or searching on these forums for (Your Video Card) + xorg.conf + ubuntu + maybe the brand of your monitor.

If you happen to be using an ATI based card (as I am), I found this tutorial immensly helpful: [http://www.ubuntuforums.org/showthread.php?t=24557&highlight=2001FP]("http://www.ubuntuforums.org/showthread.php?t=24557&highlight=2001FP")

Getting your monitor to use it's top resolution seems to be a matter of A) Having the correct or most appropriate video driver installed.  And B) Having your xorg.conf configured properly.  Hopefully you will be able to find an example out there that fits your setup.

---

