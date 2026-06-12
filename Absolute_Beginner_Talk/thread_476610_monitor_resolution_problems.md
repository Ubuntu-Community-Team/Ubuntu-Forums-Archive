---
title: "monitor resolution problems"
date: 2007-06-17
forum: Absolute Beginner Talk
---

### Post by GMachine_24 on 2007-06-17
Hi:

I had to reinstall Ubuntu (Edgy Eft) to the computer I am typing on because the hard drive fried. And, no, I didn't have a back up. I know... my bad.

Anyway, I reinstalled the software with the same hardware but can only get one - well, ok two - refresh rates as follows:

1024x768
86Hz


800 x 600
85 Hz

640x480
85 Hz


These are the readings after I ran the reconfigure setup as recommended in the Ubuntu "howto" to fix video resolutions. I set parameters for my monitor, etc. and this is a portion of my xorg.conf file:


<begin"
Section "Device"
	Identifier	"S3 Inc. 86C410 Savage 2000"
	Driver		"vesa"
	BusID		"PCI:1:0:0"
EndSection
Section "Monitor"
	Identifier	"CTX VL700"
	Option		"DPMS"
	HorizSync	30-70
	VertRefresh	50-170
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"S3 Inc. 86C410 Savage 2000"
	Monitor		"CTX VL700"
	DefaultDepth	16
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

<end>

I had saved a copy of the original xorg.conf file and this is what it says for the same portion of the file:

<begin>
Section "Device"
	Identifier	"S3 Inc. 86C410 Savage 2000"
	Driver		"savage"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-64
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"S3 Inc. 86C410 Savage 2000"
	Monitor		"Generic Monitor"
	DefaultDepth	16
	SubSection "Display"
		Depth		1
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480" "640x350"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480" "640x350"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480" "640x350"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480" "640x350"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480" "640x350"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480" "640x350"
	EndSubSection
EndSection

<end>

Before installing a new hd and reinstalling Ubuntu there were numerous refresh rates available under many different resolution settings - I know I know I will back up this time.

Thanks in advance.

PLEASE REMEMBER I HAVE GONE THROUGH THE UBUNTU "HOWTO" FIX VIDEO RESOLUTION PROBLEMS AND THINGS DID NOT GET ANY BETTER.

--gm

---

### Post by w4ett on 2007-06-17
In your terminal type: 

sudo gedit /etc/X11/xorg.conf

Copy and paste the copy of your old xorg. config into your new one...or open the old copy that you saved and save as /etc/X11?xorg.conf

this should give you back your settings.

---

### Post by GMachine_24 on 2007-06-18
Hi:

Thanks for your reply.

I guess I didn't make myself clear: I do not want the original settings. I know I can cp the xorg.conf.old file over the xorg.conf file. However, the original configuration of xorg.conf allowed me to have a refresh rate of just 60 Mhz on whatever resolution I'd choose.

Which is why I was changing the settings in xorg.conf .....

Anyone else??

--gm

---

### Post by gottatrieit on 2007-06-18
GMachine;
    I just had a major crash of my video system due to an update I didn't know how to complete properly.  i say this only to show you my problem as I'm sure you're much more competant than I am. My situation was definately my BAD, big time!!\
    I re-installed from scratch too, and my video was stuck on a resolution I didn't like so I looked back at a couple of tutorials I had referred to (for nVidia drivers) and inserted the refresh rates I wanted as well as the screen size.
    The reason I mention all this is that nVidia recommended a refresh rate of vertical refresh @ 50-77mhz.  I'm wondering if your v-rate of up to 170 is correct.  I know nothing of rates, so I'm just curious if the rates go up to three digits.

---

### Post by GMachine_24 on 2007-06-18
Hi:

Again, thanks for your comment.

I did not check the recommendations of S3 for the Savage 2000 video card in this system - I will do that. However, before the system craxhed I had the vert/horiz rates as they are now - I got them from CTX (the monitor maker) so I don't see why they shouldn't work this time - but as I said, I will check it out.

Thanks for your idea.

gm

---

### Post by GMachine_24 on 2007-06-24
If I change the horiz/vert rates I get a kaleidescope of colors cascading down my screen - which might be good if I was on LSD or something but as far as getting a computer to work, it's not that helpful.

I remember seeing a post months ago from someone with a similar video card to mine - I think the guy ended the post by saying he was just going to get another video card. No one who's serious about graphics uses a Diamond Viper/S3 2000 card - they're old but in a computer where snappy graphics aren't necessary, they work fine. Or so I thought.

Ciao bella.

---

