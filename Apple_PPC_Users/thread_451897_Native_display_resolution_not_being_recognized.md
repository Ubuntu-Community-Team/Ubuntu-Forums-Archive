---
title: "Native display resolution not being recognized?"
date: 2007-05-22
forum: Apple PPC Users
---

### Post by irskep on 2007-05-22
Just installed Ubuntutoday, but I write Mac games in my spare time, so I'm not entirely clueless. I at least got dual booting to work with no hassle.

I'm on a clunky-looking 1 gHz eMac. Ubuntu refuses to recognize any resolution besides 1024x768, even though my display's native resolution is 1280x960. I tried adding the text below to /etc/X11/xorg.conf, but it didn't do a thing. What am I missing?

```
	SubSection "Display"
		Depth		24
		Modes		"1280x960"
	EndSubSection
```

(Also, 2 other unrelated, minor things: how do you change the screen brightness a la F14, F15 in OS X, and is there software that maps the apple key to actually do something, ie be the control key also?)

---

### Post by irskep on 2007-05-23
I hate to bump threads like this, but this was about to get pushed out and I would think it's not a very obscure question.

---

### Post by mtb-cliff on 2007-05-23
I am going to guess that is the monitor section that is not being read correctly. I know that my monitor is supposed to be DPMS compliant, but I always have to manually provide the resolution and refresh rates that it will support, or I get stuck with a screen resolution that I don't want. 

Ex:

Section "Monitor"
	Identifier	"SyncMaster 900IFT"
	Option		"DPMS"
	HorizSync	30-96
	VertRefresh	50-160
EndSection

[http://www.xfree86.org/3.3.6/Config5.html#5](http://www.xfree86.org/3.3.6/Config5.html#5)

---

### Post by irskep on 2007-05-24
I have no idea how to know what my refresh rates are. The OS X monitor menu lists between 72 and 89, but I don't know if it will go higher or lower.

---

