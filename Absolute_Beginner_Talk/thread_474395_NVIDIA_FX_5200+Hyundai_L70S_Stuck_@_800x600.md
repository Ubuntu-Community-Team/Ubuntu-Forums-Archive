---
title: "NVIDIA FX 5200+Hyundai L70S: Stuck @ 800x600"
date: 2007-06-15
forum: Absolute Beginner Talk
---

### Post by ddcc on 2007-06-15
As the title of the post says, I've got a Ubuntu Feisty machine triple-booted with two Windows 2000. I've already installed Ubuntu and enabled the nvidia-glx drivers through the restricted drivers manager, however, the screen remains stuck at 800x600 @ 50hz. I've tried launching nvidia-settings in terminal and changing the resolution, but the only option available is Auto. I've also tried running sudo dpkg -reconfigure xserver-xorg, selecting nvidia and then selecting the other options including keyboard and mouse (UK keyboard, I'm in US, mouse is ps/2), but it still doesn't work. I've attached a zip of my xorg.conf.

---

### Post by freebird54 on 2007-06-15
I'm pretty sure that the problem is in the monitor configuration.  You have

```
Section "Monitor"
	Identifier	"L70S"
	Option		"DPMS"
[B]	HorizSync	28-64
	VertRefresh	43-60[/B]
EndSection
```

I have (SAMPLE ONLY)
```

Section "Monitor"
        Identifier   "Samsung_900iFT"
[B]        HorizSync    30.0 - 100.0
        VertRefresh  50.0 - 160.0[/B]
        Option      "DPMS"
SIMPLE
EndSection
```

You will notice that HorizSync and VertRefresh values on mine are **MUCH** higher, and they are what allow higher reolutions and refresh rates.  It is necessary to enter **CORRECT** values in there for **YOUR** monitor though...otherwise the magic blue smoke that makes it work might escape.  :)

If you don't have documentation for the monitor, you can usually find what you need by Googling its model number.  If that fails - then rerun the dpkg-reconfigure and select *MEDIUM* or *ADVANCED* monitor detection - it usually can work from there better than it seems to do by default, or with the [I]
SIMPLE[/I] option.  Here is a link with more detail if required...[http://users.bigpond.net.au/hermanzone/p7.html](http://users.bigpond.net.au/hermanzone/p7.html) - this can walk you through in case you missed anything when trying it before.

Hope one these helps!

---

### Post by ddcc on 2007-06-15
OK. I've modified those fields with the correct ones, Ctrl-alt-backspaced, still stuck at 800x600@50hz and auto in nvidia-settings. Any other ideas? New xorg.conf attached.

---

### Post by ddcc on 2007-06-15
I've found that running "sudo dpkg-reconfigure xserver-xorg" and selecting "nv" allows me to use 1280x1024, however, I don't have 3d acceleration, which I need.

---

### Post by ddcc on 2007-06-15
Fixed. Installed the drivers from nvidia.com.

---

