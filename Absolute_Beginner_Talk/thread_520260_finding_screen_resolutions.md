---
title: "finding screen resolutions"
date: 2007-08-08
forum: Absolute Beginner Talk
---

### Post by dascheer on 2007-08-08
i need to know what the horizontal and vertical frame rate for my screen so i can configure my screen resolution to 1280x1024.  i dont have a manual and dell doesnt list my screen's manufacturer.  

i recently re-installed ubuntu 6.10.  i have an ati radeon mobility x1300 card and my screen's 15.4" TrueLife WXGA -- whatever that means.

ive checked the forums, google, and several reference guides.  im kinda lost.  and a n00b.

---

### Post by Wim Sturkenboom on 2007-08-08
Question first:
Is the resolution listed in the *display* subsection for the *default depth*  in the *screen* section in your X configuration file? If so

The first thing you can try is to add the line
```
Option "UseEdidFreqs" "True"
``` to the *device* section in your x configuration file. This tells X to use frequencies retrieved from the monitor.

If that fails, use a modeline calculator like [http://zaph.com/Modeline/](http://zaph.com/Modeline/) to calculate the horizontal sync frequencies.
Fill in the desired resolution and vertical refresh rate and it will give you a horizontal frequency. Your monitor **will** support that frequency if it supports that resolution at that vertical refresh rate.
Do not change the other values unless you know what you're doing.

You basically have to do the calculation twice
[LIST]
[*]for the lowest resolution at the lowest vertical refresh rate
[*]for the highest resolution at the highest vertical refresh rate
[/LIST]

The first one gives you the minimum value for the horizontal sync; you can use the value that your monitor currently uses (e.g. 1024x768 ). I assume it's a TFT/LCD, so the minimum vertical refresh rate is usually 60Hz. Fill in the numbers, calculate  and you get **47.52** kHz.

The second one gives you the minimum for the maximum value for the horizontal sync. You know that the max resolution that your monitor supports is 1280x1024, so fill in those values. If you don't know the vertical refresh rate that your monitor supports, use 60 and calculate. This will give you **63.42**kHz.

Round the figures and fill in in the X configuration file
```
HorizSync 47 - 64
```

If you know that your monitor can handle 1280x1024@75Hz, only the 64 in above line changes (to about 80)

I can not help you with the vertical refresh rates (it's something you must know) to be able to do the above, but this should get you going.

Your system might still 'complain' in which case you can finetune the values in small steps.


Just in case (you might know this already):
If X does not start any longer, you can use <ctrl><alt><F1> to get to a console, login and edit the X configuration file using an editor like vi or nano)

---

### Post by kurup on 2007-08-08
> **dascheer said:**
> i need to know what the horizontal and vertical frame rate for my screen so i can configure my screen resolution to 1280x1024.  i dont have a manual and dell doesnt list my screen's manufacturer.  

i recently re-installed ubuntu 6.10.  i have an ati radeon mobility x1300 card and my screen's 15.4" TrueLife WXGA -- whatever that means.

ive checked the forums, google, and several reference guides.  im kinda lost.  and a n00b.

Do a "sudo dpkg-reconfigure xserver-xorg" at the terminal.

Default answer is Yes/OK to most of questions asked (Note: donot change to Yes/OK where the red tab is already at NO). Select Yes to write default files section to configuration file. Go ahead with the monitor detection (in this case Generic Monitor) and come down to the next screen which says 'Video Modes'. Select 1280*1024 resolution and press OK. 

The next screen is most important here in this exercise. You need to choose the option "Medium" while selecting the monitor characteristics and resolution @60Mhz. The xorg.conf will be overwritten..you need to reboot and you should now be in your desired resolution.

Have fun!

---

### Post by dascheer on 2007-08-08
hey thanks for the advice, but neither worked.  here's a copy of the device and monitor section of my xconfig file
[HTML]
Section "Device"
	Identifier	"Generic Video Card"
	Driver		"fglrx"
	BusID		"PCI:1:0:0"
	Option "UseEdidFreqs" "True"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync 	47 - 64
	VertRefresh	50-75
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Generic Video Card"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection
[/HTML]

---

### Post by amazingtaters on 2007-08-08
Ok, maybe I'm totally missing the point here, but if you wanna change your resolution can't you just go to system > preferences > screen resolution and change it from there in a jif?

---

### Post by dascheer on 2007-08-08
YEA I FIXED IT

in the reconfigure xserver thing i just deselected the other resolutions i didnt want. YEAASAAAA

---

### Post by ekss on 2007-08-09
thanx a lot kurup!

---

### Post by kurup on 2007-08-09
> **ekss said:**
> thanx a lot kurup!
Welcome! Getting the right resolution in the end is such a high!

---

### Post by Jim Danner on 2007-08-09
Can you help me with a similar problem? I have a monitor that works best at 60 Hz, but the only option for refresh rate listed in the Screen Resolution preference box is 75 Hz.

I ran "sudo dpkg-reconfigure xserver-xorg" and explicitly selected the 60 Hz rate (with 1280x1024 as the resolution, which is also set as the maximum resolution). After it finished, it had put these lines in xorg.conf:
> 	HorizSync	30-65
	VertRefresh	50-75
(Nothing else had changed.) But in Screen Resolution, it was still 75 Hz only.

The HorizSync maximum does look like the calculation result that Wim Sturkenboom posted above. Should I change VertRefresh as well? To a maximum of 60? What is the best thing to try next?

*Edit* Tried setting VertRefresh to 60 and HorizSync to 64, still no change.

---

### Post by Wim Sturkenboom on 2007-08-09
The only good indication of the vertical refresh rate is on your screen (OSD), not a function somewhere in Gnome or KDE.

---

### Post by Jim Danner on 2007-08-09
> **Wim Sturkenboom said:**
> The only good indication of the vertical refresh rate is on your screen (OSD), not a function somewhere in Gnome or KDE.

OK, fair enough. The OSD of my monitor reports: 1280x1024@75Hz. In the xorg.conf file I now have these lines:
```

	HorizSync	30-64
	VertRefresh	50-60
```

What other options do I have?

---

### Post by Wim Sturkenboom on 2007-08-10
Try if adding *Option "UseEdidFreqs" "FALSE"* to the device section helps. If not, I don't know.
If it does not help, I'm at a loss. Let us know the result.

---

### Post by Jim Danner on 2007-08-10
Well... no luck with that either.

Thanks anyway, who knows I'll find a solution at some point.

---

### Post by Jim Danner on 2007-10-19
Well, Ubuntu 7.10 has solved the problem. It has better drivers, I guess. After installation the refresh frequency was set to the optimal 60 Hz. Well done developers!

---

