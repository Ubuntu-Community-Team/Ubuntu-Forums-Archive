---
title: "Please Explain This"
date: 2006-12-27
forum: Absolute Beginner Talk
---

### Post by Stephen47 on 2006-12-27
I am trying to get my resoultion straightened out. Here are the relevant parts of my Xorg file:

Section "Device"
	Identifier	"Intel Corporation Mobile Integrated Graphics Controller"
	Driver		"i810"
	BusID		"PCI:0:2:0"
	Option		"UseFBDev"		"true"
EndSection
Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-84
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation Mobile Integrated Graphics Controller"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1680x1050"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1680x1050"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1680x1050"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1680x1050"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1680x1050"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1680x1050"
	EndSubSection

________________________________________________________________________________________-

Section "Device"
	Identifier	"Intel Corporation Mobile Integrated Graphics Controller"
	Driver		"i810"
	BusID		"PCI:0:2:0"
	Option		"UseFBDev"		"true"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-84
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation Mobile Integrated Graphics Controller"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1680x1050"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1680x1050"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1680x1050"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1680x1050"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1680x1050"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1680x1050"
	EndSubSection
EndSection
The section above the line is the file when I first boot. The resoultion is 1280x 1024. 
The section below the line is the file after I run:
"sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.custom
sudo sh -c 'md5sum /etc/X11/xorg.conf > /var/lib/x11/xorg.conf.md5sum'
sudo dpkg-reconfigure xserver-xorg"
which gives me the resolution of 1680x1050 which is what I want. 
As you can see the files are exactly the same. Why wont Ubuntu Boot to the 1680x1050 resolution?

---

### Post by Stephen47 on 2006-12-28
bump anyone?

---

### Post by po0f on 2006-12-28
Stephen47,

I hear [915resolution](http://packages.ubuntu.com/edgy/x11/915resolution) solves this problem.

---

### Post by Stephen47 on 2006-12-29
no it doesn't it is temporary also. I would like to know why the xorg.conf file is the same in both cases.

---

### Post by Stephen47 on 2006-12-30
So there is no solution to this problem? I am stuck having to run:sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.custom
sudo sh -c 'md5sum /etc/X11/xorg.conf > /var/lib/x11/xorg.conf.md5sum'
sudo dpkg-reconfigure xserver-xorg
every time I boot?

---

### Post by macogw on 2006-12-30
915resolution does fix it.  I think you have to set it up for 915resolution to run on startup though, otherwise it reverts to 1024x768 after a reboot.

---

### Post by Stephen47 on 2006-12-30
So what am I running that corrects the problem? And can I set that to run at startup and if so how do I do that?

---

