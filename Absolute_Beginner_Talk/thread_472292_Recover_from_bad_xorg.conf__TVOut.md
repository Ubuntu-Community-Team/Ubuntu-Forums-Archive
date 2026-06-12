---
title: "Recover from bad xorg.conf / TVOut"
date: 2007-06-12
forum: Absolute Beginner Talk
---

### Post by kellygreer1 on 2007-06-12
What are the steps to recover from a bad xorg.conf? command line and copy backup to original xorg.conf? or is there a wizard or steps to reprobe my card to rewrite the file? 

I was trying to use the aticonfig cli tool to get my TVOut working on my ATI Radeon X1300 card.
Any advice on the best way to set this up? I don't need my monitor after I get the s-video to my CRT.
Any links to xorg.conf that will work for this?  I saw a few posts in these forums but the things I tried didn't work.

Thanks in advance,
Kelly (KellyGreer1)

---

### Post by 67GTA on 2007-06-12
You can boot into recovery mode and run "sudo dpkg-reconfigure xserver-xorg". That will take you through the steps to reconfigure your xorg.conf file. I don't know anything about the TV/out part. My ATI TV tuner is not supported, so never had to set it up.

---

### Post by kellygreer1 on 2007-06-12
thanks for the tip on recovering the xorg.conf I may try this on the next run.

Using this post almost exactly:
[http://ubuntuforums.org/showthread.php?t=209024](http://ubuntuforums.org/showthread.php?t=209024)
I was getting an X Server startup error.
Any one have any thoughts on this setup? Its not quite what I needed I just need the TV but I thought this was a good place to start. I have had both the monitor and the s-video connected during my tests.

Kelly

---

### Post by kellygreer1 on 2007-06-12
Ok.  I located some error output.

I have a few lines that may help:
(WW) fglrx: No matching Device section found for instance (BusID PCI:1:0:1)
(EE) fglrx(0): PreInitDAL failed
(EE) fglrx(0): PreInit failed

Kelly

---

### Post by kellygreer1 on 2007-06-13
Can anyone spot an error in my file? Still getting the last set of errors?

# relevant part of file starts here

Section "Device"
	Identifier	"ATI Video Card"
	Driver		"fglrx"
	Busid		"PCI:1:0:0"
	Screen		0     
EndSection

Section	"Device"
	Identifier	"ATI tvout"
	Driver		"fglrx"
	BusID		"PCI:1:0:1"
	Screen		1
	Option		"TVOutFormat"	"SVIDEO" #COMPOSITE SVIDEO RGB
	Option		"TVStandard"	"NTSC-M"
	Option		"ConnectedMonitor"	"TV"
EndSection

Section "Monitor"
	Identifier	"SyncMaster"
	Option		"DPMS"
EndSection

Section "Monitor"
	Identifier	"TV"
	Option		"HorizSync"	"30-50"
	Option		"VertRefresh"	"50"
EndSection

Section "Screen"
	Identifier	"Screen0"
	Device		"ATI Video Card"
	Monitor		"SyncMaster"
	Defaultdepth	24
	SubSection "Display"
		Depth	1
		Modes		"1680x1050"	"1280x1024"	"1280x960"	"1152x864"	"1024x768"	"832x624"	"800x600"	"720x400"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	4
		Modes		"1680x1050"	"1280x1024"	"1280x960"	"1152x864"	"1024x768"	"832x624"	"800x600"	"720x400"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	8
		Modes		"1680x1050"	"1280x1024"	"1280x960"	"1152x864"	"1024x768"	"832x624"	"800x600"	"720x400"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	15
		Modes		"1680x1050"	"1280x1024"	"1280x960"	"1152x864"	"1024x768"	"832x624"	"800x600"	"720x400"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	16
		Modes		"1680x1050"	"1280x1024"	"1280x960"	"1152x864"	"1024x768"	"832x624"	"800x600"	"720x400"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	24
		Modes		"1680x1050"	"1280x1024"	"1280x960"	"1152x864"	"1024x768"	"832x624"	"800x600"	"720x400"	"640x480"
	EndSubSection
EndSection

Section	"Screen"
	Identifier	"Screen1"
	Device		"ATI tvout"
	Monitor		"TV"
	DefaultDepth	24
	SubSection	"Dsiplay"
	Depth		24
	Modes		"640x480"
#	Modes		"800x600"
	EndSubsection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen 0 "Screen0"
	Screen 1 "Screen1" rightOf "Screen0"
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

---

### Post by kellygreer1 on 2007-06-13
I corrected the misspelled "display" and still does not work. same errors as above.
Also not sure about the PCI:1:0:1 or keeping them both PCI:1:0:0.  Neither seem to work.

I previously had setup on this box openSUSE 10.2 and it worked after getting the proprietary drivers from ATI's website and just setting the display to 800x600.  Didn't seem to have to do anything to setup the s-video.  Should I re-install openSUSE on this machine just to steal the xorg.conf file? or could there be other factors at play?

Kelly

---

### Post by kellygreer1 on 2007-06-13
Well, because I wanted to check out Fedora 7 ... I just tried that instead of the openSUSE 10.2.  

No luck. :(

Thursday I'll reinstall openSUSE 10.2 to this machine and grab the xorg.conf file.

Hope I can get the TV Out to work with Ubuntu ... (and with this Radeon X1300 card)

Kelly

---

