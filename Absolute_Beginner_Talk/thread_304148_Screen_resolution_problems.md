---
title: "Screen resolution problems"
date: 2006-11-21
forum: Absolute Beginner Talk
---

### Post by gweiss on 2006-11-21
I'm new to Ubuntu and I'm using a widescreen notebook with maximum 1280 x 768 resolution. Graphics is the Intel GMA 900. I have the display driver for it, according to Synaptic, and my xorg.conf lists 1280 x 768: 

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x768"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x768"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x768"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x768"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x768"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x768"
	EndSubSection
EndSection

But I can't change the screen resolution above (or, for that matter, below) 1024 x 768 using System --> Preferences --> Screen Resolution. Is there another way to change the screen resolution? How can I change it to 1280 x 768? Note that I used to use Mandriva before switching to Ubuntu, and that distro used 1280 x 768 by default.

---

### Post by Bachstelze on 2006-11-21
Please paste the whole file. Also, I think [this](http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=915&searchon=names&subword=1&version=all&release=all) might interest you.

---

### Post by gweiss on 2006-11-21
Hi, I finally got it working. While posting the original message I installed xserver-xorg-video-intel on Synaptic, which is apparently an alternate driver for my chipset. A restart and it's 1280 x 768. Thanks so much for your help, though!

---

### Post by John E on 2006-11-21
This seems to be a major drawback with Ubuntu. My display wouldn't go above 640 x 480 - even though my graphics card & monitor are both capable of 2048 x 1536.

I did find that if I installed Fedora immediately before installing Ubuntu, Ubuntu would work in whatever resolution had been set by Fedora. But of course, I can't keep installing Fedora every time I need to change screen resolution... :(

---

### Post by Bachstelze on 2006-11-21
Install proper drivers for your card, just like he did...

---

### Post by John E on 2006-11-21
I've just been to the Matrox web site and downloaded the Linux drivers for my card - but how do I go about installing the right driver? There seem to be about 20 files all zipped up in a tar file. :confused:

---

### Post by Bachstelze on 2006-11-21
The Matrox drivers are available as binaries, but you'll need to use the command line to install them...

---

### Post by John E on 2006-11-21
Come back MS-DOS, all is forgiven... where do I find out the relevant commands?

---

### Post by Bachstelze on 2006-11-21
[http://www.tuxx-home.at/projects/mtx/latest/readme.txt](http://www.tuxx-home.at/projects/mtx/latest/readme.txt)

---

### Post by John E on 2006-11-21
Thanks for the link. I really am very grateful for the help - even though it does feel like I'm stepping back 20 years in time! :)

---

