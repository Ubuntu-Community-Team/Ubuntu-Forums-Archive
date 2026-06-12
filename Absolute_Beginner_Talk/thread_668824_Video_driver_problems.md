---
title: "Video driver problems"
date: 2008-01-15
forum: Absolute Beginner Talk
---

### Post by me_weird on 2008-01-15
I know, you've probably been asked this a million times.
Installed Gutsy, and it's working fine except for my screen resolution.  It's too high, and my driver won't let me go down to a lower resolution.  I've had the misfortune to have gone through two hard drives with Windows in the past few years, so I know that to fix this in windows I needed to hunt around online and find a new video driver.  I went through the steps in the ubuntu wiki to get new nVidia drivers...but when I go to "Restricted Device Manager" like the wiki says I get an error that says I don't need any restricted drivers.
Dunno if it's helpful, but here's the sections of xorg.conf that seem to be relevant:
Section "Device"
	Identifier	"Generic Video Card"
	Driver		"vesa"
	BusID		"PCI:1:0:0"
EndSection
Section "Screen"
	Identifier	"Default Screen"
	Device		"Generic Video Card"
	Monitor		"E70-10"
	DefaultDepth	24
	SubSection "Display"
		Modes		"1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
EndSection
Sorry for asking what's probably a really stupid question, but it gives me such a headache to work on this screen and I just can't seem to figure out what else to do.  Thanks in advance for your help.

---

### Post by nikoPSK on 2008-01-15
You can reconfigure xorg like this:

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

nikoPSK

---

### Post by PeterJS on 2008-01-15
That would be the right set up for a generic video card, what video card do have?
```

lspci | grep VGA

```

---

### Post by me_weird on 2008-01-15
Dude you guys are awesome for replying so fast.
Compy says I have this kind of video card:
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon RV200 QW [Radeon 7500]

---

### Post by PeterJS on 2008-01-15
There is in fact not a restricted driver for that card. The documentation says that card is supported:
[https://help.ubuntu.com/community/RadeonDriver#head-93fc0a86162afbf71a5b84eff7da6c6a338656b1](https://help.ubuntu.com/community/RadeonDriver#head-93fc0a86162afbf71a5b84eff7da6c6a338656b1)

Since you don't have the fglrx drivers installed you can skip straight to the configuring X step:
[https://help.ubuntu.com/community/RadeonDriver#head-7e2283943de094f4c373154f2e8178bfa9374050](https://help.ubuntu.com/community/RadeonDriver#head-7e2283943de094f4c373154f2e8178bfa9374050)

---

### Post by me_weird on 2008-01-15
Wonderfully gave me a nice high refresh rate (before I could only get 60Hz, now the only option is 85Hz)...but for some reason will only give 800x600 as my max resolution.  Any suggestions?

---

### Post by nikoPSK on 2008-01-15
> **me_weird said:**
> Wonderfully gave me a nice high refresh rate (before I could only get 60Hz, now the only option is 85Hz)...but for some reason will only give 800x600 as my max resolution.  Any suggestions?

you've gone to system, preferences, screen resolution?

---

### Post by me_weird on 2008-01-15
Yeah.  Well it also gives 640x480 as an option... but that's it.  Nothing higher.

---

