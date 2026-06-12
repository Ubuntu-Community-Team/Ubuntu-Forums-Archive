---
title: "Dual screen/TwinView"
date: 2005-10-09
forum: Absolute Beginner Talk
---

### Post by boohiss on 2005-10-09
I have onboard nvidia which supports two monitors.  I guess what I had before in Windows was called "TwinView", or one big desktop that spans two monitors.

I've already installed the "nvidia" driver, and I'm now using it instead of "nv".  I've googled all over the place to see how to get the second screen to work and to get the X desktop extended over there, but so far nothing I've done to xorg.conf has helped (except for changing "nv" to "nvidia" which worked nicely, and I now get an nvidia logo when X starts).

Any ideas on how to do this?

---

### Post by ngms27 on 2005-10-09
This works for me:

Section "Files"
	FontPath	"unix/:7100"			# local font server
	# if the local font server has problems, we can fall back on these
	FontPath	"/usr/lib/X11/fonts/misc"
	FontPath	"/usr/lib/X11/fonts/cyrillic"
	FontPath	"/usr/lib/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/lib/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/lib/X11/fonts/Type1"
	FontPath	"/usr/lib/X11/fonts/CID"
	FontPath	"/usr/lib/X11/fonts/100dpi"
	FontPath	"/usr/lib/X11/fonts/75dpi"
        # paths to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
EndSection

Section "Module"
	Load	"bitmap"
	Load	"dbe"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"record"
	Load	"type1"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"keyboard"
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
	Option		"Protocol"		"ImPS/2"
	Option		"Emulate3Buttons"	"true"
	Option		"ZAxisMapping"		"4 5"
EndSection

Section "Device"
	Identifier	"NVIDIA Corporation NV18 [GeForce4 MX - nForce GPU]"
	Driver		"nvidia"
	BusID		"PCI:2:0:0"
EndSection

Section "Monitor"
	Identifier	"Acer AL1912"
	Option		"DPMS"
	HorizSync	24-80
	VertRefresh	49-75
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NV18 [GeForce4 MX - nForce GPU]"
	Monitor		"Acer AL1912"
	DefaultDepth	24
        Option "NvAGP" "0"
        Option "HWCursor" "true"
        Option "ConnectedMonitor" "CRT-0, CRT-1"
        Option "TwinView" "true"
        Option "SecondMonitorHorizSync" "31.5 - 70"
        Option "SecondMonitorVertRefresh" "85"
        Option "MetaModes" "1280x1024, 1024x768; 1280x1024, 1280x1024; 1024x768, 1024x768; 1024x768, 800x600"
        Option "TwinViewOrientation" "LeftOf"
	SubSection "Display"
		Depth		1
		Modes		"1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
EndSection



Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		0 "Default Screen"
        InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
EndSection

Section "DRI"
	Mode	0666
EndSection

Two LCD 19 inch screens.

JonnyT

---

### Post by mlomker on 2005-10-09
> Any ideas on how to do this?

The key is the left/right paramaters in the Serverlayout section.  [Here's an article]("http://72.14.203.104/search?q=cache:cr6qnGiobm0J:www.linux-magazine.com/issue/17/DualHead.pdf+serverlayout+right+left&hl=en&client=firefox") about it.

---

### Post by boohiss on 2005-10-09
[QUOTE=ngms27]This works for me:

...

Two LCD 19 inch screens.

JonnyT[/QUOTE]

Thanks for your quick response.  I copied/pasted most of your xorg.conf file into my own, still with no results.  I've read through the nvidia README now about a dozen times, and I just can't figure out what I'm missing or not doing right.

Any other ideas?

Thanks,

boohiss

P.S.  Did I mention the dual video is onboard and not two cards?

---

### Post by JakeSpeare on 2005-10-11
you may want to try adding a second videocard definition, ie a second "Device" section listing specs again, but with a slightly changed identifier name.

---

### Post by poofyhairguy on 2005-10-11
I love my spanning dual head set up. I used this page to get it to work:

[http://gentoo-wiki.com/HOWTO_Dual_Monitors](http://gentoo-wiki.com/HOWTO_Dual_Monitors)

It applies all the same for Ubuntu since they both use xorg. If you can't grok it, or it gives you problems I can give you my xorg.conf.

---

### Post by boohiss on 2005-10-11
[QUOTE=poofyhairguy]I love my spanning dual head set up. I used this page to get it to work:

[http://gentoo-wiki.com/HOWTO_Dual_Monitors](http://gentoo-wiki.com/HOWTO_Dual_Monitors)

It applies all the same for Ubuntu since they both use xorg. If you can't grok it, or it gives you problems I can give you my xorg.conf.[/QUOTE]

I think I understand it just fine, but it just doesn't work!  Could you please show me your xorg.conf?  I've already looked at about a dozen, but I guess one more couldn't hurt!

Thanks

---

### Post by JakeSpeare on 2005-10-11
Have a look at this post:

[http://ubuntuforums.org/showthread.php?p=393341#post393341]("http://ubuntuforums.org/showthread.php?p=393341#post393341")

---

### Post by boohiss on 2005-10-12
[QUOTE=JakeSpeare]Have a look at this post:

[http://ubuntuforums.org/showthread.php?p=393341#post393341]("http://ubuntuforums.org/showthread.php?p=393341#post393341")[/QUOTE]

Alrighty!  I'm finally getting some results.  I have two functional screens now, with one desktop stretched across both.  The only problem now is that the left screen is 1280x1024 and the right screen is 800x600.  (This is certainly better than before, but not as good as it could be).

I think I've narrowed down the problem to the following:

Section "Screen"
	Identifier "Screen0"
	Device "videocard0"
	Monitor "Monitor0"
	DefaultDepth 16
	SubSection "Display"
		Depth 1
		Modes "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth 4
		Modes "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth 8
		Modes "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth 15
		Modes "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth 16
		Modes "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth 24
		Modes "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "Screen"
	Identifier "Screen1"
	Device "videocard1"
	Monitor "Monitor1"
	DefaultDepth 16
	Subsection "Display"
		Viewport 0 0
		Depth 16
		Modes "800x600" "640x480"
	EndSubSection
EndSection

The problem is that if I add "1024x768" and/or "1280x1024" to Screen1's Modes, I get a blank monitor1 at best, or worst, a very buggy/messed up monitor0 and blank monitor1.  Any ideas?  I'm pretty sure monitor1 is capable of at least 1024x768, but it's possible that it's not capable of 1280x1024 (it's pretty old).

---

### Post by JakeSpeare on 2005-10-12
you may want to add horizontal and vertical refresh parameters to your file.  In certain cases that makes a difference.  I don't have a reference handy, but a forum search should get you details.

---

### Post by JakeSpeare on 2005-10-12
found a link:

[URL="http://ubuntuforums.org/showthread.php?t=73099"]
http://ubuntuforums.org/showthread.php?t=73099[/URL]

---

### Post by boohiss on 2005-10-12
[QUOTE=JakeSpeare]you may want to add horizontal and vertical refresh parameters to your file.  In certain cases that makes a difference.  I don't have a reference handy, but a forum search should get you details.[/QUOTE]

That did the trick!

Thanks very much everyone who posted in this thread.  Ubuntu has been my best Linux experience so far, in large part to this forum.

---

