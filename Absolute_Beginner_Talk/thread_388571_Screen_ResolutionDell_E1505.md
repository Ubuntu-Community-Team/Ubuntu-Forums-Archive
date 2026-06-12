---
title: "Screen Resolution:Dell E1505"
date: 2007-03-19
forum: Absolute Beginner Talk
---

### Post by altrock78 on 2007-03-19
Heres my xorg file:

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1680x1050"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1680x1050"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1680x1050"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1680x1050"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1680x1050"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1680x1050"
	EndSubSection
EndSection

Im running a dell with an WXGA? monitor.  It is capable of 1680x1050, but only shows up as 1024x768.  Can anyone help me fix this issue?  Thanks

---

### Post by Kobalt on 2007-03-19
Open a Terminal and type this :
```
sudo dpkg-reconfigure -phigh xserver-xorg
```
Select the resolutions you want as available by hitting the space bar, then press Enter. 
Finally, restart X with Ctrl+Alt+Backspace.

---

### Post by annda on 2007-03-19
what is your video card? maybe you need a driver...

---

### Post by altrock78 on 2007-03-19
> **annda said:**
> what is your video card? maybe you need a driver...

Im only using the integrated Intel graphics card that comes with the 945 chipset

---

### Post by altrock78 on 2007-03-19
> **Kobalt said:**
> Open a Terminal and type this :
```
sudo dpkg-reconfigure -phigh xserver-xorg
```
Select the resolutions you want as available by hitting the space bar, then press Enter. 
Finally, restart X with Ctrl+Alt+Backspace.

Im getting this:

ubuntu@ubuntu:~$ sudo dpkg-reconfigure -phigh xserver-xorg
xserver-xorg postinst warning: not updating /etc/X11/X; file has been
   customized
xserver-xorg postinst warning: overwriting possibly-customised configuration
   file; backup in /etc/X11/xorg.conf.20070319174443
ubuntu@ubuntu:~$ 



Im using feisty BTW

---

### Post by annda on 2007-03-19
what happened after X restart/reboot?

> **altrock78 said:**
> Im only using the integrated Intel graphics card that comes with the 945 chipset

sorry, i somehow missed that in your xorg.conf. synaptic tells me that 915resolution supports your chipset. if you haven't had a success yet, try installing that.

---

### Post by altrock78 on 2007-03-19
> **annda said:**
> what happened after X restart/reboot?



sorry, i somehow missed that in your xorg.conf. synaptic tells me that 915resolution supports your chipset. if you haven't had a success yet, try installing that.

915resolution didnt seem to do anything even after a ctrl alt backspace restart

---

### Post by fxars on 2007-08-15
Has their been anything new with this issue?  I'm interested in fixing thsi problem in my Dell 1505.

---

