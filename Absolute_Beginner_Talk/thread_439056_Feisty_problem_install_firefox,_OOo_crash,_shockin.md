---
title: "Feisty problem install: firefox, OOo crash, shocking graphics..."
date: 2007-05-10
forum: Absolute Beginner Talk
---

### Post by readitsideways on 2007-05-10
Hi

After a very easy Feisty install I've tried to install Feisty on a new machine and it's pretty terrible-

The screen has messy vertical lines every inch or so - I gather it's the crappy SIS drivers so I'm getting a GF card. Hopefully that works.

Another problem is that Firefox and OOo crash when I try to open them. They start opening, but then just disappear!?!?

Any ideas?

Duncan

---

### Post by Maylar on 2007-05-10
system specs?

---

### Post by taurus on 2007-05-10
What happens if you run firefox from a terminal so you can see the error message?

Applications -> Accessories -> Terminal
```
firefox
```

---

### Post by readitsideways on 2007-05-10
I installed a Nvidia card and the graphics are now great!

However Firefox and OOo and Epiphany browser all crash on start up. Ive run updates with the update manager so everything should be up to date.

> 
What happens if you run firefox from a terminal so you can see the error message?

Applications -> Accessories -> Terminal
Code:

firefox

Nothing happens at all. Not even the task bar "Starting Firefox" button.

This is really frustrating as all the essential programs like Firefix and OOo are not working...!?!?

Thanks

Duncan

Duncan

---

### Post by readitsideways on 2007-05-11
How would I find what the error is - what log can I look at?

---

### Post by readitsideways on 2007-05-11
Ok, now I'm worried: it does the same thing from the live CD. Firefox won't open.

Intel Core Duo 3Gh
512 M RAM
NVIDIA 6200 graphics card

---

### Post by readitsideways on 2007-05-11
Reinstalled Firefox (can't uninstall as EVERYTHING depends on it - including the Ubuntu desktop) and still the same problem: certain apps just won't start:

Firefox
OOo
Epiphany

Getting ready to put XP on...

---

### Post by readitsideways on 2007-05-11
I've just noticed that in my hardware info my Nvidia 6200 is showing, but so is the SiS IDE (is that the old SiS graphics card?).. Could this have something to do with it

If I can't fix this today I'm going to have to (sadly) switch to XP...

---

### Post by readitsideways on 2007-05-11
Opera also won't start...

---

### Post by Najand on 2007-05-11
Are you using some input method package like scim?

---

### Post by readitsideways on 2007-05-11
> Najand  	Are you using some input method package like scim?

I don't know what that is - how do I tell?

---

### Post by Najand on 2007-05-11
OK. then you don&#8217;&#65364;.
Can you type firefox in a terminal and send us the error message?

---

### Post by readitsideways on 2007-05-11
When I type firefox in a terminal nothing happens - it just goes immediately to the next prompt.

This also happens running from the Live CD

Also OOo does the same thing, and Thunderbird, and Opera

---

### Post by Najand on 2007-05-11
Are you using some desktop effects like beryl, etc?

---

### Post by readitsideways on 2007-05-11
I am, but I've tried with desktop effects on and off. As mentioned earlier, this also happens running on the Live CD with nothing installed

---

### Post by readitsideways on 2007-05-11
Hi

my thinking is: maybe because the ubuntu desktop depends on firefox, it something to do with my Nvidia card.

As detailed above, the SiS card just wasn't working so I put an Nvidia 6200 in. I had to edit the xorg.conf file to disable the SiS card:

Here's the graphics/display part:

```
Section "Device"
	Identifier	"Generic Video Card"
	Driver		"nvidia"
	#	BusID		"PCI:1:0:0"
	Option		"NvAGP"	"1"
	Option		"AddARGBVisuals"	"True"
	Option		"AddARGBGLXVisuals"	"True"
	Option		"NoLogo"	"True"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	Horizsync	28-51
	Vertrefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Generic Video Card"
	Monitor		"Generic Monitor"
	Defaultdepth	24
	SubSection "Display"
		Depth	1
		Modes		"1024x768"	"800x600"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	4
		Modes		"1024x768"	"800x600"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	8
		Modes		"1024x768"	"800x600"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	15
		Modes		"1024x768"	"800x600"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	16
		Modes		"1024x768"	"800x600"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	24
		Modes		"1024x768"	"800x600"	"640x480"
	EndSubSection
EndSection

```

---

