---
title: "Strange Resolution Settings"
date: 2007-05-12
forum: Absolute Beginner Talk
---

### Post by MOkAONE on 2007-05-12
i have a 17" CRT monitor and before, the highest setting for resolution was 1280x1024 (windows and ubuntu). i recently updated to Feisty and that was still the highest setting (downloaded version of Feisty), but once i got the Live CD version in the mail.. and after installing my video card drivers via Envy i can set it to 1680x1050, 1400x1050 and a couple of other random settings. the weird thing is, my monitor can actually handle up to 1680x1050.

my question is, is there any way i can have it run at like 1680x **** ... something closer to 3:4 ratio? maybe by manually editing the xorg.conf file, and if so.. wat resolution would it be?

edit: btw.. i have a ATi 9600 Pro, which according to the website it can handle the following resolutions.

1280x1024 
1600x1024
1600x1200
1792x1344
1856x1392
1920x1080
1920x1200* 
1920x1440 
2048x1152 
2048x11280 
2048x1536

*1920 x 1200 flat panel resolution available through use of reduced blanking interval.

---

### Post by strikeback03 on 2007-05-13
1600x1200 is the common 3:4 ratio for that approximate resolution.  Suppose you could try manually adding 1680x1260.

---

### Post by MOkAONE on 2007-05-13
hmm... i tried manually editing the the xorg.conf file, but theres nothing there. its blank. o_0 ??

---

### Post by strikeback03 on 2007-05-13
want to post a copy of your xorg.conf?  for example, here is what the relevant section of mine looks like:
```
Section "Screen"
	Identifier	"Default Screen"
	Device		"nVidia Corporation G70 [GeForce 7600 GT]"
	Monitor		"FPD2485W"
	Defaultdepth	24
	SubSection "Display"
		Depth	1
		Modes		"1680x1680"	"1600x1200"	"1440x1440"	"1400x1050"	"1280x1024"	"1152x864"	"1024x768"	"832x624"	"800x600"	"720x400"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	4
		Modes		"1680x1680"	"1600x1200"	"1440x1440"	"1400x1050"	"1280x1024"	"1152x864"	"1024x768"	"832x624"	"800x600"	"720x400"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	8
		Modes		"1680x1680"	"1600x1200"	"1440x1440"	"1400x1050"	"1280x1024"	"1152x864"	"1024x768"	"832x624"	"800x600"	"720x400"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	15
		Modes		"1680x1680"	"1600x1200"	"1440x1440"	"1400x1050"	"1280x1024"	"1152x864"	"1024x768"	"832x624"	"800x600"	"720x400"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	16
		Modes		"1680x1680"	"1600x1200"	"1440x1440"	"1400x1050"	"1280x1024"	"1152x864"	"1024x768"	"832x624"	"800x600"	"720x400"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	24
		Modes		"1920x1200" "1680x1680"	"1600x1200"	"1440x1440"	"1400x1050"	"1280x1024"	"1152x864"	"1024x768"	"832x624"	"800x600"	"720x400"	"640x480"
	EndSubSection
EndSection
```

I added the 1920x1200 to the last depth to run my monitor

---

### Post by Pobega on 2007-05-13
You may want to dpkg-reconfigure xserver-xorg, and select the correct information. Usually when it comes to fixing resolutions that does the trick, since the generic xserver installation can't encompass EVERY option, so it chooses the most general.

---

### Post by akschnare on 2007-05-13
Hey, I have the Radeon 9600XT and was wondering if I can still change the resolutions if I just keep the default driver that comes with Ubuntu. I ask because when I install the ATI driver with Envy, I can get the 1920 x 1200 resolution for my monitor, but I can't use the desktop effects.

I just installed Beryl, and was wondering if that will work with the new driver instead of using the basic desktop effects. Thanks for any help.

---

