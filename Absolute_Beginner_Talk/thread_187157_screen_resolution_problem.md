---
title: "screen resolution problem"
date: 2006-06-02
forum: Absolute Beginner Talk
---

### Post by jwillmo on 2006-06-02
I've just installed ubuntu onto my hp pavilion n5495 laptop and can't get it to display at 1400X1050 so I'm left with a black frame around the screen. 

Initially in preferences/screen res I had only 1 option - 1280x1024. Now, I can't be sure because I've tried a number of things but following this guide 

[https://wiki.ubuntu.com/FixVideoResolutionHowto?highlight=%28resolution%29](https://wiki.ubuntu.com/FixVideoResolutionHowto?highlight=%28resolution%29) and inputting horiz and vert refresh rates into xconfig 

seemed to enable me to select a number of different resolutions - although unfortunately all lower than the 1280x1024 already selected.

my xconfig now looks like this (I'm not 100% sure about the refresh rates but think they are correct - couldn't find the spec on the internet anywhere) with the horizsync and vert refresh lines being new additions

Section "Device"
	Identifier	"Intel Corporation 82830 CGC [Chipset Graphics Controller]"
	Driver		"i810"
	BusID		"PCI:0:2:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync          30-75
	VertRefresh        50-85
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation 82830 CGC [Chipset Graphics Controller]"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1400x1050"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1400x1050"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1400x1050"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1400x1050"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1400x1050"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1400x1050"
	EndSubSection

I have also tried running 855resolution and that now looks like this...

#
# 855resolution default
#
# find free modes by  /usr/sbin/855resolution -l
# and set it to MODE
#
MODE=3c
#
# and set resolutions for the mode.
#
XRESO=1400
YRESO=1050

However if I run 855resolution -l it doesn't seemed to have registered this..

Chipset: Unknown (id=0x35758086)
VBIOS type: 3
VBIOS Version: 2501

Mode 30 : 640x480, 8 bits/pixel
Mode 31 : 640x400, 8 bits/pixel
Mode 32 : 800x600, 8 bits/pixel
Mode 34 : 1024x768, 8 bits/pixel
Mode 36 : 1024x600, 8 bits/pixel
Mode 38 : 1280x1024, 8 bits/pixel
Mode 3a : 1600x1200, 8 bits/pixel
Mode 3c : 1920x1440, 8 bits/pixel
Mode 40 : 640x480, 15 bits/pixel
Mode 41 : 640x480, 16 bits/pixel
Mode 42 : 800x600, 15 bits/pixel
Mode 43 : 800x600, 16 bits/pixel
Mode 44 : 1024x768, 15 bits/pixel
Mode 45 : 1024x768, 16 bits/pixel
Mode 46 : 1024x600, 15 bits/pixel
Mode 47 : 1024x600, 16 bits/pixel
Mode 48 : 1280x1024, 15 bits/pixel
Mode 49 : 1280x1024, 16 bits/pixel
Mode 4a : 1600x1200, 15 bits/pixel
Mode 4b : 1600x1200, 16 bits/pixel
Mode 4c : 1920x1440, 15 bits/pixel
Mode 4d : 1920x1440, 16 bits/pixel
Mode 50 : 640x480, 32 bits/pixel
Mode 52 : 800x600, 32 bits/pixel
Mode 54 : 1024x768, 32 bits/pixel
Mode 56 : 1024x600, 32 bits/pixel
Mode 58 : 1280x1024, 32 bits/pixel
Mode 5a : 1600x1200, 32 bits/pixel
Mode 5c : 1920x1440, 32 bits/pixel

So if i type 855resolution 3c 1400 1050, I get the following...

Chipset: Unknown (id=0x35758086)
VBIOS type: 3
VBIOS Version: 2501

** Patch mode 3c to resolution 1400x1050 complete
 
but then if I get the list again it hasn't changed; i.e. mode 3c is still 1920x1440.

Being new to Linux and ubuntu just to get this far has taken me absolutely ages so I would be massively grateful for any help anyone can give me.

James

---

### Post by snorlax on 2006-06-02
Try this:

sudo dpkg-reconfigure xserver-xorg. 

You'll get a series of screens. Keep everything at the default until you reach the driver list.  Set it to VESA.
Keep going with the monitor, mouse, and keyboard defaults, and say yes to writing the settings to the config files.

Opt NOT to autodetect the monitor.

Enter a name for it
BIG: In the screen after monitor naming, select the resolution(s) you would want your screen to display.
Then choose MEDIUM info in the subsequent display that shows "Simple, Medium, Advanced" and enter your screen size.

I am away from the linux computer right now but remember the steps well enough, I think.
I just did this yesterday on a laptop and it worked; hope it will help you as well. 

Jim

---

### Post by jwillmo on 2006-06-02
Thanks Jim, I tried that but seem to have a problem with xserver-xorg - I received this message:

Package `xserver-xorg.' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
/usr/sbin/dpkg-reconfigure: xserver-xorg. is not installed

When I go to Synaptic it says there are a number of errors (see below for small selection) but xserver-xorg is definitely installed.

W: Couldn't stat source package list [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) breezy/main Packages (/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_breezy_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) breezy/restricted Packages (/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_breezy_restricted_binary-i386_Packages) - stat (2 No such file or directory)

Any suggestions?

---

### Post by jwillmo on 2006-06-03
Again, thanks Jim.

Solved the synaptic problem with this: sudo apt-get update

Was able to run the xserver-xorg when I typed it in correctly (I cut n' pasted and left the .  at the end!)

However when I applied the changes and restarted, the black edge had definitely gone but the whole screen was light brown with nothing else at all visible.

Bizarrely I entered my username and password anyway and there slowly emerged the very faintest outline of an old word document - one that I'm sure isn't even on this PC anymore! But that image slowly faded till the whole screen was again light brown.

Can anyone help?

---

### Post by jwillmo on 2006-06-05
One final try...

The strange thing is I feel I'm nearly there because when I run xserver-xorg all the options are already set to 1400x1050 so at some level it seems to have correctly detected the resolution, chipset and driver etc. 

It just seems to be getting stuck somewhere. 

Also infuriating is that I feel if it could just save the changes to the modes when I run 855resolution that might sort it.

James

---

### Post by shanerdaner on 2007-04-21
Hi did you ever get this fixed?  I had to format over because I couldn't see anything it was all white screen.

---

