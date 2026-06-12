---
title: "nvidia problems"
date: 2008-02-09
forum: Absolute Beginner Talk
---

### Post by dysolve on 2008-02-09
Hello all,
 I tried to setup my system for dual monitor so i backed up xorg.conf and had a play with nvidia-setting then i rebooted only to get my second crt monitor working but my main benq fp202w just said out of range and did not display gui. so i replaced the new xorg with my backed up copy and my system now displays the same thing on both monitors but @ 640 res and every time i try to change anything the benq goes back to out of range... i even tried to reconfig xorg.conf and the same issue applies.. the next idea i had was to boot from live cd a steal the xorg.conf from that that works with dual monitors but again when i reload the system from my hdd it shows out of range on the benq monitor and it crt is @ 640.. if anybody knows a fix for this please let me know..

thanks in advance 
david.

---

### Post by PmDematagoda on 2008-02-09
Are you using the Nvidia driver when trying to setup the dual screens?

Also, if you are using the Nvidia driver, could you post how you set it up and also what your Nvidia VGA card is.

---

### Post by dysolve on 2008-02-09
thanks for the reply..

i have a 8800gtx 320meg card

i tried to set it up with the nvida control panel..
gsudo nvidia-setting..

---

### Post by PmDematagoda on 2008-02-09
If you restart Ubuntu does Ubuntu still use the Nvidia driver or does the X-Server crash?

---

### Post by overdrank on 2008-02-09
> **PmDematagoda said:**
> If you restart Ubuntu does Ubuntu still use the Nvidia driver or does the X-Server crash?

Hi and to add to PmDematagoda could you post your xorg, with this command in the terminal ```
cat /etc/X11/xorg.conf
```
Edit sorry I thought you could get to the desktop (GUI )

---

### Post by dysolve on 2008-02-09
x-server does not crash its still working because i still get the gui logon and it plays the startup tune.. and even thought my screen tells me its out of range i can still here the "keysounds" if i login to the gui but with a terminal prompt the prompt opens in a small window so it aprears i am getting the res i want and i can still open nautilus and stuff from the command prompt.. I am in windows at the moment so i will reboot in to ubuntu now.. whats the command to run firefox from the prompt?
also if i try to open the nvidia control panel a box popups that tells me i am not running the nvidia drivers

---

### Post by dysolve on 2008-02-09
i just booted in to ubuntu and my second monitor seems to be working ok.. below is a copy of my xorg.conf file

[I]Section "Device"
	Identifier	"nVidia Corporation G80 [GeForce 8800 GTS]"
	Driver		"nvidia"
EndSection

Section "Device"
	Identifier	"Videocard0"
	Boardname	"nv"
	Busid		"PCI:7:0:0"
	Driver		"nvidia"
	Screen	0
EndSection

Section "Device"
	Identifier	"Videocard1"
	Boardname	"nv"
	Busid		"PCI:7:0:0"
	Driver		"nvidia"
	Screen	1
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"nVidia Corporation G80 [GeForce 8800 GTS]"
	Monitor		"Generic Monitor"
	Defaultdepth	24
	Option		"AddARGBVisuals"	"True"
	Option		"AddARGBGLXVisuals"	"True"
	Option		"NoLogo"	"True"
	SubSection "Display"
		Depth	24
		Modes		"nvidia-auto-select"
	EndSubSection
EndSection

Section "Screen"
	Identifier	"Screen0"
	Device		"Videocard0"
	Monitor		"Monitor0"
	Defaultdepth	24
	Option		"TwinView"	"0"
	Option		"metamodes"	"CRT-1: 1680x1050_60 +0+0; CRT-1: nvidia-auto-select +0+0"
	SubSection "Display"
		Depth	24
		Virtual	1792	1344
		Modes		"1600x1200@60"	"1792x1344@60"	"1600x1200@65"	"1400x1050@75"	"1400x1050@60"	"1280x960@75"	"1280x1024@60"	"1280x960@60"	"1280x1024@75"	"1152x864@75"	"1024x768@60"	"1024x768@70"	"1024x768@75"	"832x624@75"	"800x600@60"	"800x600@75"	"800x600@72"	"800x600@56"	"640x480@75"	"640x480@72"	"640x480@60"
	EndSubSection
EndSection

Section "Screen"
	Identifier	"Screen1"
	Device		"Videocard1"
	Monitor		"Monitor1"
	Defaultdepth	24
	Option		"TwinView"	"0"
	Option		"metamodes"	"CRT-0: nvidia-auto-select +0+0"
	SubSection "Display"
		Depth	24
		Virtual	1400	1050
		Modes		"1280x1024@60"	"1400x1050@60"	"1280x960@60"	"1152x864@75"	"1024x768@43"	"1024x768@60"	"1024x768@70"	"1024x768@75"	"1024x768@85"	"832x624@75"	"800x600@60"	"800x600@85"	"800x600@75"	"800x600@72"	"800x600@56"	"640x480@85"	"640x480@75"	"640x480@72"	"640x480@60"
	EndSubSection
EndSection[/I]

can you see anything funny with that?? the only thing i noticed is that my primary monitor which is a benq tft fp202w is CRT-1.. does make a differance?

---

### Post by overdrank on 2008-02-09
> **dysolve said:**
> i just booted in to ubuntu and my second monitor seems to be working ok.. below is a copy of my xorg.conf file
```

[I]Section "Device"
	Identifier	"nVidia Corporation G80 [GeForce 8800 GTS]"
	Driver		"nvidia"
EndSection

Section "Device"
	Identifier	"Videocard0"
	Boardname	"nv"
	Busid		"PCI:7:0:0"
	Driver		"nvidia"
	Screen	0
EndSection

Section "Device"
	Identifier	"Videocard1"
	Boardname	"nv"
	Busid		"PCI:7:0:0"
	Driver		"nvidia"
	Screen	1
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"nVidia Corporation G80 [GeForce 8800 GTS]"
	Monitor		"Generic Monitor"
	Defaultdepth	24
	Option		"AddARGBVisuals"	"True"
	Option		"AddARGBGLXVisuals"	"True"
	Option		"NoLogo"	"True"
	SubSection "Display"
		Depth	24
		Modes		"nvidia-auto-select"
	EndSubSection
EndSection

Section "Screen"
	Identifier	"Screen0"
	Device		"Videocard0"
	Monitor		"Monitor0"
	Defaultdepth	24
	Option		"TwinView"	"0"
	Option		"metamodes"	"CRT-1: 1680x1050_60 +0+0; CRT-1: nvidia-auto-select +0+0"
	SubSection "Display"
		Depth	24
		Virtual	1792	1344
		Modes		"1600x1200@60"	"1792x1344@60"	"1600x1200@65"	"1400x1050@75"	"1400x1050@60"	"1280x960@75"	"1280x1024@60"	"1280x960@60"	"1280x1024@75"	"1152x864@75"	"1024x768@60"	"1024x768@70"	"1024x768@75"	"832x624@75"	"800x600@60"	"800x600@75"	"800x600@72"	"800x600@56"	"640x480@75"	"640x480@72"	"640x480@60"
	EndSubSection
EndSection

Section "Screen"
	Identifier	"Screen1"
	Device		"Videocard1"
	Monitor		"Monitor1"
	Defaultdepth	24
	Option		"TwinView"	"0"
	Option		"metamodes"	"CRT-0: nvidia-auto-select +0+0"
	SubSection "Display"
		Depth	24
		Virtual	1400	1050
		Modes		"1280x1024@60"	"1400x1050@60"	"1280x960@60"	"1152x864@75"	"1024x768@43"	"1024x768@60"	"1024x768@70"	"1024x768@75"	"1024x768@85"	"832x624@75"	"800x600@60"	"800x600@85"	"800x600@75"	"800x600@72"	"800x600@56"	"640x480@85"	"640x480@75"	"640x480@72"	"640x480@60"
	EndSubSection
EndSection[/I]
```

can you see anything funny with that?? the only thing i noticed is that my primary monitor which is a benq tft fp202w is CRT-1.. does make a differance?

No the xorg looks good as I see. When you reconfigured your xorg did you use this command
```
sudo dpkg-reconfigure -phigh xserver-xorg
``` And how did you install the drivers, did you use the restricted drivers?

---

### Post by dysolve on 2008-02-09
i did install the restricted driver but that only gave me single monitor, so i played with the nvidia control panel and now i have the issues.. but if i revert back to my old xorg.conf i am still in troble..

---

### Post by overdrank on 2008-02-09
> **dysolve said:**
> i did install the restricted driver but that only gave me single monitor, so i played with the nvidia control panel and now i have the issues.. but if i revert back to my old xorg.conf i am still in troble..

Ok you may look at Envy
[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

---

### Post by dysolve on 2008-02-11
i did the envy installed now once i enter my username and password my CRT monitor turns off and my LCD still tells me its out of range!

---

### Post by dysolve on 2008-02-12
i found that if i turn twinview on it works fine but I am stuck running the same res accros both monitors.. its something like 1960*1060.. but it works.. I want to be able to run both monitors @ different res.

---

