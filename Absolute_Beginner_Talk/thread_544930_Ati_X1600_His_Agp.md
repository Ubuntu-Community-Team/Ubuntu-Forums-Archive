---
title: "Ati X1600 His Agp"
date: 2007-09-06
forum: Absolute Beginner Talk
---

### Post by FAILINX on 2007-09-06
I thought you might be interested in reading this web page:
[http://www.driverheaven.net/showthread.php?t=141921&referrerid=133412](http://www.driverheaven.net/showthread.php?t=141921&referrerid=133412)
I HAVE A HIS X 1600 CARD AGP.  I RECENTLY INSTALLED THE LATEST VERSION OF UBUNTU(FIESTY FAWN). AFTER SELECTING UBUNTU FROM THE DUAL BOOT MENU,IT STATES LOADING... THEN IMMEDIATLY CRASHES.  THE SCREEN DOESNT GO BLACK ITS AS IF THE CARD JUST ISNT PLUGGED IN.  ITS DIAGONAL SCROLLING LINES.  INEED TO BE ABLE TO FIX THE PROBLEM FROM RECOVERY MODE CUS I CANT GET INTO G EDIT OR BY ANY OTHER MEANS I HAVE SEEN, OR DISCUSSED.  HAVE TRIED THE ALTERNATIVE INSTALL WITH THE SAME RESULTS/ IF ANYONE HAS ANY IDEAS PLEASE LET ME KNOW THANKS--F
From,
FAILINX

---

### Post by FAILINX on 2008-01-20
I have gotten everything to work.  If I can help anyone who is have trouble with the ati x1600. let me know. you may post here if you want on the card and other issues as they relate.  The newest problem I am having is both my laptop <dell inspiron running gutsy with comiz, and the destop running beryl with atix1600> both go into sleep mode for no reason. Both are set 
to NEVER go into sleep mode and the screen savers are disabled.  If anyone has ideas on that
I would appreciate it.  Thanks,--F  Also how do you network the two. both are online but cannot "see" each other.:KS

---

### Post by kellemes on 2008-01-20
For other people's information, and mine ;-)
I'm having this issue with my x1650.

Can you please post /etc/X11/xorg.conf
and find out the version of the driver you're using? (I assume it's fglrx?)


Thanks.

---

### Post by FAILINX on 2008-01-28
kell, i am running fiesty with xgl session, and the fglrx driver. Oddly enough compiz is loaded but not running.  I hope I can help. Sorry, I didnt track my work well enough to write a good walk through so we will have to reverse engineer this one.  I only hope i can help.  I will look through my book marks and see if I can find the source of my driver downloads.  Anyways, ask all you want on my system files.  I will gladly share them with all because I know how irritating this was for me, and can only assume there are others pulling their hair out.  Here is my xorg.conf:

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
	Load		"i2c"
	Load		"bitmap"
	Load		"ddc"
	Load		"dri"
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
	Option          "VBERestore"    "yes"
EndSection

Section "Device"
	Identifier	"Generic Video Card"
	Driver		"fglrx"
	Busid		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	Horizsync	28-64
	Vertrefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Generic Video Card"
	Monitor		"Generic Monitor"
	Defaultdepth	24
	SubSection "Display"
		Depth	1
		Modes		"1280x1024"	"1152x864"	"1024x768"	"832x624"	"800x600"	"720x400"	"640x480"	"640x400"	"640x350"
	EndSubSection
	SubSection "Display"
		Depth	4
		Modes		"1280x1024"	"1152x864"	"1024x768"	"832x624"	"800x600"	"720x400"	"640x480"	"640x400"	"640x350"
	EndSubSection
	SubSection "Display"
		Depth	8
		Modes		"1280x1024"	"1152x864"	"1024x768"	"832x624"	"800x600"	"720x400"	"640x480"	"640x400"	"640x350"
	EndSubSection
	SubSection "Display"
		Depth	15
		Modes		"1280x1024"	"1152x864"	"1024x768"	"832x624"	"800x600"	"720x400"	"640x480"	"640x400"	"640x350"
	EndSubSection
	SubSection "Display"
		Depth	16
		Modes		"1280x1024"	"1152x864"	"1024x768"	"832x624"	"800x600"	"720x400"	"640x480"	"640x400"	"640x350"
	EndSubSection
	SubSection "Display"
		Depth	24
		Modes		"1280x1024"	"1152x864"	"1024x768"	"832x624"	"800x600"	"720x400"	"640x480"	"640x400"	"640x350"
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
Section "Extensions"
	Option		"Composite"	"0"
EndSection

For what its worth I do know that under the first section the GLX and DRI commands are key.  
Good Luck, lemme know if it helps and if you have any ideas on how to prevent sleep mode.   Between that and networking I am staying pretty busy.  Thanks for the reply -F

---

### Post by FAILINX on 2008-01-28
Oh, I forgot I am using the ATI restricted drivers packages as well.  THIS IS FOR ANYONE INTERSTED: Here are a few of the tutorials i followed on the way.  No one tutorial was a solution in itself, but I got it to work so here they are in order.

[http://ubuntuforums.org/showthread.php?t=399643&highlight=x200m](http://ubuntuforums.org/showthread.php?t=399643&highlight=x200m)

[http://forum.beryl-project.org/viewtopic.php?f=36&t=3228&st=0&sk=t&sd=a&sid=10f9412c1b7a85d7f8d8fd9a70b5bd0f&start=10](http://forum.beryl-project.org/viewtopic.php?f=36&t=3228&st=0&sk=t&sd=a&sid=10f9412c1b7a85d7f8d8fd9a70b5bd0f&start=10)

[http://ubuntuforums.org/showthread.php?p=2895086](http://ubuntuforums.org/showthread.php?p=2895086)


Too bad about Beryl.  I think its way better rendering than compiz.

---

