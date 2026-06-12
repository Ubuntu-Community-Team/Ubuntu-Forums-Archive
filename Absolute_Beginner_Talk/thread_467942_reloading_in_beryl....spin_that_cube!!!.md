---
title: "reloading in beryl....spin that cube!!!"
date: 2007-06-08
forum: Absolute Beginner Talk
---

### Post by dyno_eq on 2007-06-08
hi,
 Just wandered if anyone can explain to me what reloading options in beryl means wehn i type beryl in the terminal? and what options i have? i can get it all to work fine but it stops when i close the terminal window that i started it on. Can i keep it open all the time even when i log back on? And why did it get rid of the minimise maximise and close button in the top right hand corner?

thanks everyone for the help so far

---

### Post by Zzl1xndd on 2007-06-08
when you installed Beryl did you install the Manager & Emerald as well?

---

### Post by starcraft.man on 2007-06-08
> **dyno_eq said:**
> hi,
 Just wandered if anyone can explain to me what reloading options in beryl means wehn i type beryl in the terminal? and what options i have? i can get it all to work fine but it stops when i close the terminal window that i started it on. Can i keep it open all the time even when i log back on? And why did it get rid of the minimise maximise and close button in the top right hand corner?

thanks everyone for the help so far


Ok, I think you got a bit ahead of yourself... the minimize max buttons disappearing means you didn't edit the xorg for Beryl. I assume you have the drivers, else you'd have crash the comp.

Open up the terminal and please follow along: terminal is Applications > Accessories > Terminal.

BEFORE doing this, if you don't have an Nvidia card tell me. I believe you need different entries modified. This is **ONLY for Nvidia** cards I think (well first step anyway).

1) ```
gksudo gedit /etc/X11/xorg.conf

```
When that opens up, scroll down to the section titled "Device" and paste this in the bottom (right above End Section).
		
```
Section "Device"
	Identifier	"nVidia Corporation NV40 [GeForce 6800 GT]"
	Driver		"nvidia"
	BusID		"PCI:1:0:0"
	[COLOR="Red"]Option          "TripleBuffer" "true"[/COLOR]
EndSection
```

Next scroll down to the bottom of the screen section and paste in the two red commands I have shown here:

```
Section "Screen"
	Identifier	"Default Screen"
	Device		"nVidia Corporation NV40 [GeForce 6800 GT]"
	Monitor		"VP930 Series"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x1024" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
[COLOR="Red"]    	Option "AddARGBGLXVisuals" "True"
    	Option "DisableGLXRootClipping" "True"[/COLOR]
EndSection
```

Make sure they line up the same as in my example, your card and screen will likely be different so mine is just an example.

Then push the save button and close.

2) Install manager and emerald

type this command into the terminal:

```
sudo aptitude install beryl beryl-manager emerald-themes
```

That will ensure you have everything installed.

3) Go System > Preferences > Sessions

Now you have to set it to start up. You need 2 entries. Push New, title it Beryl and make the command "beryl-manager". Then ok, then make another new one. Title this one Emerald, the command is "emerald --replace".

Push ok, close all your windows and reboot. That should do it. Please follow it to the letter....

Oh and yes you can leave Beryl on all the time, I do and I find its quite stable. Once ya get that installed and rebooted ok tell me. I have a few more tweaks to tell ya about to make it smooth.

---

### Post by Zzl1xndd on 2007-06-08
Starcraftman 

I mentioned that because the last time I tryed to install beryl I did it Via Synaptic and and for got those other parts and had this exact problem.

---

### Post by starcraft.man on 2007-06-08
> **tweakedenigma said:**
> Starcraftman 

I mentioned that because the last time I tryed to install beryl I did it Via Synaptic and and for got those other parts and had this exact problem.

Right, wuups, I was actually meaning to quote the OP hehe... got the wrong quote. You were fine, its just I always edit the xorg first before putting Beryl in.

There... edited :).

---

