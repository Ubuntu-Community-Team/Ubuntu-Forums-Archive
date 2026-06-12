---
title: "Inspiron 9300 screen resolution problems"
date: 2007-07-30
forum: Absolute Beginner Talk
---

### Post by duncancan on 2007-07-30
hi everybody,

i'm sorry for the annoying question, and i hope this isn't more than a teething problem; i've very recently installed ubuntu studio onto my laptop. it's a dell inspiron 9300, with an nvidia 6800 go, and a WUXGA (1920*1200) 17" screen.

the problem is, i can't get it to run at 1920*1200; by looking [here]("http://fluffi.info/inspiron9300/single/"), and the XF86Config-4 therein, i've put in the correct horizontal sync and vertical refresh values (either by running *sudo dpkg-reconfigure xserver-xorg* from the command line and going through the advanced configuration, or just editing /etc/X11/xorg.conf), i've been able to get the refresh rate up from 61Hz to 86Hz (woo), but i still can't get it to run at a resolution higher than 1280*1024.

here's the relevant section from my xorg.conf, if it helps:

```
Section "Device"
	Identifier	"NVidia GeForce 6800"
	Driver		"vesa"
	BusID		"PCI:1:0:0"
	Option		"UseFBDev"		"true"
EndSection

Section "Monitor"
	Identifier	"DELL Panel WUXGA"
	Option		"DPMS"
	HorizSync	28-110
	VertRefresh	43-90
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVidia GeForce 6800"
	Monitor		"DELL Panel WUXGA"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1920x1200" "1680x1050"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1920x1200" "1680x1050"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1920x1200" "1680x1050"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1920x1200" "1680x1050"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1920x1200" "1680x1050"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1920x1200" "1680x1050"
	EndSubSection
EndSection
```

and at the risk of making this post seem too big and long, i have two problems which i assume are much simpler, just because i'm a linux newby: 

1. i want ALSA to load my PCMCIA soundcard module (snd-indigoio), instead of loading the onboard soundchip's module. where do i alter which module is loaded on boot? 

2. there's a computer in my study, a canon pixma ip4000, and it's connected to a windows computer. i want to print from it -- is this possible? its network address is \\study\printer.


sorry i'm such a newbie! [http://ubuntuforums.org/images/smilies/icon_sad.gif](http://ubuntuforums.org/images/smilies/icon_sad.gif)

thanks everybody,
-duncan

---

### Post by w4ett on 2007-07-30
You are using the Vesa driver, which is the most basic video driver It only provides 2d support...To get full use of your card's capabilities you will need to enable your restricted drivers:  under System>Administration>Restricted Drivers Manager  or use the Envy install Script:

[http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)


Lets get your video running first  :)

---

### Post by splintercellguy on 2007-07-30
What a coincidence! I happen to have the same printer as you. I believe it is simply a matter of System->Administration->Printers and adding a printer.

---

### Post by duncancan on 2007-07-30
hey, thanks w4ett! envy's a really, really amazing program. so, uh, yeh. that's solved the resolution issue.

now all i need to know is how to make the kernel load the snd-indigoio module, and i have a problem with the printer still:

i have it set up as a network printer (windows (SMB)), and all that's working fine as far as i can tell, but no matter what i try to print, or what paper source i select in the printer properties (cassette,  auto sheet feeder, etc etc) the windows computer to which the printer is connected comes up with an error on its screen saying: 

"a paper size that cannot be fed from the cassette was selected". 

the cassette is the paper source from windows, too, and it works, and it has lots of paper in it.

thanks again,
-duncan

---

### Post by w4ett on 2007-07-30
> **duncancan said:**
> hey, thanks w4ett! envy's a really, really amazing program. so, uh, yeh. that's solved the resolution issue.

now all i need to know is how to make the kernel load the snd-indigoio module, and i have a problem with the printer still:

i have it set up as a network printer (windows (SMB)), and all that's working fine as far as i can tell, but no matter what i try to print, or what paper source i select in the printer properties (cassette,  auto sheet feeder, etc etc) the windows computer to which the printer is connected comes up with an error on its screen saying: 

"a paper size that cannot be fed from the cassette was selected". 

the cassette is the paper source from windows, too, and it works, and it has lots of paper in it.

thanks again,
-duncan

I'm not a printer guy, so why not start a new thread with your additional issues?

Good luck

---

