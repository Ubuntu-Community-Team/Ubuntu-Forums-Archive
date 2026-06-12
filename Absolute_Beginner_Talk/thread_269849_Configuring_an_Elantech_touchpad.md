---
title: "Configuring an Elantech touchpad"
date: 2006-10-02
forum: Absolute Beginner Talk
---

### Post by lalji on 2006-10-02
I can't seem to find any drivers for this touchpad, or much discussion of it at all either on the forum or elsewhere. Does anyone have any hints for configuring an Elantech touchpad on Ubuntu? I want to manipulate the settings for things like scrolling via using two fingers etc.

---

### Post by Or'Enn on 2006-11-11
Also wondering the same. The laptop is a Compal HEL80. The touchpad goes crazy at times.

```
Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizScrollDelta"	"0"
	Option		"MaxTapTime"		"0"
	Option		"Emulate3Buttons"	"off"
EndSection
```

---

### Post by kwilliam on 2007-03-07
Other than the touchpad, how well does (K)Ubuntu run on the HEL80?  I'm considering buying one.  Did wireless work out-of-the-box?  (Is there anything that doesn't work?)

---

### Post by lalji on 2007-06-28
I have a Compal HGL30 and ubuntu has generally run pretty well. When I installed Dapper Drake I had to configure the nvidia drives and had touchpad issues (mine also would go nuts), but those problems are both gone now with Feisty Fawn. In addition, I got rid of the trash icon from my toolbar because when the touchpad would go crazy it would open up ten copies of the trash folder - it can't do that without the icon there. In any case, FF doesn't seem to generate the same touchpad issues for me.

---

### Post by linuxonbute on 2008-01-30
See this thread, it might help.

[http://ubuntuforums.org/showthread.php?t=681553&highlight=elantech](http://ubuntuforums.org/showthread.php?t=681553&highlight=elantech)

---

