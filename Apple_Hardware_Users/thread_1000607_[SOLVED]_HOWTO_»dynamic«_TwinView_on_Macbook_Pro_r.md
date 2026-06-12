---
title: "[SOLVED] HOWTO: »dynamic« TwinView on Macbook Pro running Intrepid (8.10)"
date: 2008-12-03
forum: Apple Hardware Users
---

### Post by __david on 2008-12-03
Hello everybody,

yesterday I succeeded making TwinView recognize different external Monitors on my MacBook Pro. Since I had not found a suitable thread on this forum, I&#8217;m hoping this post will be useful to others.

[SIZE="3"]Introduction[/SIZE]
Unfortunately, the binary nvidia driver doesn&#8217;t support hotplugging of external Display devices through RandR which would be very useful for laptops. On the other hand, the free »nv« driver does not support suspend.

While it&#8217;s perfectly possible to use nVidias TwinView technology you have to specify a list of »MetaModes« in xorg.conf, that is, specify a fixed monitor setup.

[SIZE="3"]Tested configuration[/SIZE]
The following configuration has been tested on a MacBook Pro 4,1 (»Penryn«) running Intrepid Ibex (Ubuntu 8.10) And using the latest proprietary nVidia driver (177.80). I have a few MacTel-PPA packages installed, but consider that not essential for this HowTo. 

This HowTo *should* work on every MacBook with nVidia graphic chip, allthough I don&#8217;t know that and therefore don&#8217;t take any responsibility for **your** specific hardware setup.

I&#8217;m using my MacBook Pros display (»DFP-0«), and (at home) a flat panel to the left of the laptop (»DFP-1«) or a LCD-TV right of the computer, which is connected to the MBP through a VGA-Cable (and therefore regarded as »CRT-0« by the nVidia driver).

[SIZE="3"]Getting everything running[/SIZE]
To be clear: this tutorial won&#8217;t make your setup hotplug-aware. Any external display you&#8217;re going to use has to be connected when X starts up. But at least you will be more flexible connecting external displays to your MBP &#8230;

We&#8217;ll start with the minimalistic xorg.conf Intrepid provides. The section for your nVidia card should look similar to mine:
```
Section "Device"
	Identifier	"Configured Video Device"
	Driver	"nvidia"
	Option	"NoLogo"	"True"
EndSection
```

Activate TwinView by adding the following option to the section:
```
	Option		"TwinView"			"True"
```

Then, figure out the arrangement of your displays. The nVidia driver uses the following order when calculating the orientation: CRT (every device connected through a VGA cable), DFP-0 (the MBPs main screen), DFP-1 (every external screen connected through a DVI cable). Since my external display (DFP-1) is to the left of my MBP (DFP-0), I&#8217;m using »LeftOf«. This will also work for my TV (on the right), because the MBP (DFP-0) is to the left of it (CRT-0). Awesome.

Add:
```
	Option		"TwinViewOrientation"		"LeftOf"
```
You can also use one of "RightOf" (the default), "Above", or "Below".


At the end, we&#8217;ll specify which display to use as primary device (where the gnome panels will be placed etc.). This is competely independent of the orientation order.

Add the following:
```
	Option		"TwinViewXineramaInfoOrder"	"DFP-1, DFP-0, CRT"
```
This will make an external flat panel connected through DVI the primary display (if connected), or will use the MBPs display in other cases. Change that line to suit your needs.

That&#8217;s it. We&#8217;re done. [SIZE="2"]**Don&#8217;t use any MetaModes**[/SIZE].

When connecting a device, you will have to restart the X Server (log out and in once). I can live with that.

[SIZE="3"][COLOR="Red"]WARNING[/COLOR][/SIZE]
Don&#8217;t disconnect an external display and reconnect another while X is running! 
This *could* cause damage to your displays due to improper device timings and resolutions. 

If you want to disconnect a display and immediately reconnect another, you should either use the nvidia-settings GUI tool (and use »detect devices« and »apply« *before* plugging in another display), or disconnect external display &#8211; restart X &#8211; connect other device &#8211; restart X.

[SIZE="3"]xorg.conf[/SIZE]
At the end, your xorg.conf should look something like this:
```
Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	DefaultDepth	24
EndSection

Section "Module"
	Load	"glx"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver	"nvidia"
	Option	"NoLogo"	"True"
	Option		"TwinView"			"True"
	Option		"TwinViewOrientation"		"LeftOf"
	Option		"TwinViewXineramaInfoOrder"	"DFP-1, DFP-0, CRT"
EndSection
```

---

