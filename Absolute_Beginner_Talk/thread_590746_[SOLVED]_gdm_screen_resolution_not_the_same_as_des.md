---
title: "[SOLVED] gdm screen resolution not the same as desktop environment"
date: 2007-10-25
forum: Absolute Beginner Talk
---

### Post by unebaguettesvp on 2007-10-25
so, i've read through all the posts on the forums regarding the gdm screen resolution not being the same as the screen resolution of the desktop. they ALL say to remove the unwanted screen resolution modes from the xorg.conf file. I DID THAT. here is the relevant section:

```
Section "Monitor"
	Identifier	"LCD MONITOR"
	Option		"DPMS"
	HorizSync	30-70
	VertRefresh	50-87
	# 1280x720 @ 60.00 Hz (GTF) hsync: 44.76 kHz; pclk: 74.48 MHz
	Modeline "1280x720_60.00"  74.48   1280 1308 1444 1664    720  721  724  746  -HSync +Vsync
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies Inc Radeon R350 [Radeon 9800 Pro]"
	Monitor		"LCD MONITOR"
	DefaultDepth	24
	SubSection "Display"
		Depth		24
		Modes		"1280x720_60.00"
	EndSubSection
EndSection
```

I have a 720p projector and I can display the desktop in 1280x720 just fine. But in the GDM screen, the screen is 1280x720 shrunk to 1024x768. The display is 1024, whats inside the display looks like 1280. It almost looks like an hourglass shape.

Any ideas?

Note: This only started happening since I installed a brand new Gutsy. I never had this problem with Feisty or Edgy.

---

### Post by unebaguettesvp on 2007-10-25
please help! thanks!

---

### Post by unebaguettesvp on 2007-10-25
sorry for the bump. anyone have any ideas?

---

### Post by unebaguettesvp on 2007-10-25
sorry for another bump again. but i need something to test out when i get home. thanks for any help.

---

### Post by kellemes on 2007-10-25
In your Display-section.. have you tried adding... (In between *Depth* and *Modes*)
```
virtual 1280 720
```

And should.. ```
1280x720_60.00
``` not be like.. ```
1280x720@60.00
```
Not sure about this one..

---

### Post by unebaguettesvp on 2007-10-25
that's actually a good idea to try out. i've read here:

[https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/146828]("https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/146828")

that the Virtual setting has been giving people problems. maybe it will do the opposite for me. thanks!

---

### Post by unebaguettesvp on 2007-10-25
Adding "Virtual" worked!!!! Now, my xorg.conf file looks like this:

```
Section "Monitor"
	Identifier	"LCD MONITOR"
	Option		"DPMS"
	HorizSync	30-70
	VertRefresh	50-87
	# 1280x720 @ 60.00 Hz (GTF) hsync: 44.76 kHz; pclk: 74.48 MHz
	Modeline "1280x720_60.00"  74.48   1280 1308 1444 1664    720  721  724  746  -HSync +Vsync
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies Inc Radeon R350 [Radeon 9800 Pro]"
	Monitor		"LCD MONITOR"
	DefaultDepth	24
	SubSection "Display"
		Depth		24
		Virtual		1280	720
		Modes		"1280x720_60.00"
	EndSubSection
EndSection
```

Thank you so much!!!!

---

### Post by likemindead on 2007-10-29
Think this might work for me? What exactly would I need to change? Here's my current:

```
Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies Inc M10 NT [FireGL Mobility T2]"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Modes		"1600x1200"
	EndSubSection
EndSection
```

Thanks!

---

