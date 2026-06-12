---
title: "Ubuntu - Screen Resolution"
date: 2005-09-20
forum: Absolute Beginner Talk
---

### Post by MuRRe on 2005-09-20
Have installed Ubuntu but a made  a mistake. I choose the wrong resolution and now i cant change it to the one i want. Where do i change this??

---

### Post by FLeiXiuS on 2005-09-20
In the top left gnome-panel.  

You'll see system.

System > Preferences > Screen Resolution

---

### Post by DoeRayMe on 2005-09-20
I have a similer problem, but i cant change resoluation, only has 640-480 availible

Is this normal or can it be fixed?

---

### Post by ispmarin on 2005-09-20
Please, tell us what is your video card and append your /etc/X11/xorg.conf to see what can be the problem.

Ivan

---

### Post by DoeRayMe on 2005-09-20
i have an intergrated Intel 82845G Graphics/Video Card

cant copy as its on another computer

---

### Post by MuRRe on 2005-09-21
I have an ATI x700 128 MB. Th problem is my keyboard wouldnt respond on installion so i just freaked out and pushed ALL buttons.
I fond the file:
Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies, Inc. Radeon Mobility X700 (RV410)"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1920x1440" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1920x1440" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1920x1440" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1920x1440" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1920x1440" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1920x1440" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection
 But I can't change in it...???

---

### Post by weasel fierce on 2005-09-21
You need to open the file as root, sudo and then the command that opens it

---

### Post by openmind on 2005-09-21
You need to manually enter the Horizsync and Vertrefresh rates for your monitor.

---

### Post by PsyberOneZero on 2005-09-21
Also, which driver are you using for the card? 
I had a similar prob. with nVidia, it defaulted to "vesa" driver.
The card might not work well with the ati or vesa drivers.  You probably will have to install the fglrx drivers.

---

### Post by MuRRe on 2005-09-21
[QUOTE=weasel fierce]You need to open the file as root, sudo and then the command that opens it[/QUOTE]
I went in to the Root Termina. For the there i searched my way to the file. But when i open it it doesn't show anything.
(gedit:8221): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.

What should i do to open as Root?

---

### Post by Vicsun on 2005-09-21
[QUOTE=MuRRe]I went in to the Root Termina. For the there i searched my way to the file. But when i open it it doesn't show anything.
(gedit:8221): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.

What should i do to open as Root?[/QUOTE]
Have you tried
```
sudo gedit <filename>
```

---

### Post by PsyberOneZero on 2005-09-21
You could also use (Applications->System->Run ad different user), type gedit in the box, make sure root is selected in the drop down box and hit OK, enter your password and your good to go.

---

