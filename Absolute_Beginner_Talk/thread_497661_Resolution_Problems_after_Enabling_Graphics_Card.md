---
title: "Resolution Problems after Enabling Graphics Card"
date: 2007-07-10
forum: Absolute Beginner Talk
---

### Post by Matt Nichols on 2007-07-10
So I recently realized that my Nvidia Graphics Card was not in use, so I went to System>Administration>Restricted Drivers Manager, and clicked the Enabled box under "Nvidia Accelerated Graphics Driver (legacy cards)", and it installed the driver just fine. Now, after rebooting, my computer is in 800x600 resolution, and won't go any higher using System>Preferences>Screen Resolution. This is very frustrating! Everything is too big! I really want to be able to use this card, but if this is the price, I don't know if I can do it. Can you help me find the best of both worlds? What is wrong? Thanks, any help is greatly appreciated.

(By the way, I am using Ubuntu Feisty Fawn on a desktop, for what it's worth)

---

### Post by tarek on 2007-07-10
You need to edit xorg.conf:
```
gksudo gedit /etc/X11/xorg.conf
```

Find:
```

Section "Screen"
	Identifier	"Default Screen"
	Device		"Generic Video Card"
	Monitor		"KM-718"
	DefaultDepth	24
	SubSection "Display"
		Depth		24
		Modes		"1024x768" "800x600" "640x480"
	EndSubSectionplay"

```

You should see that you only have 800x600 so add 1024x768.

Restart gnome:
```
Control + Alt + Backspace
```

TK

---

### Post by Matt Nichols on 2007-07-10
Excellent, that worked perfectly, thank you! I now have a sucessful resolution of 1024x768. Do you know of any way to get it even higher? I tried adding higher resolutions into the same file, but it does not seem to work that way.

---

### Post by tarek on 2007-07-10
Something like: 1152x864

```
Modes		"1152x864" "1024x768" "800x600" "640x480"
```

and so on. It should work but you might find that the refresh rate is low.

---

### Post by Matt Nichols on 2007-07-10
It didn't work. I editied the file and restarted Gnome, but still the same options. Oh well, I guess I can live with this resolution.... Thanks for the help.

---

