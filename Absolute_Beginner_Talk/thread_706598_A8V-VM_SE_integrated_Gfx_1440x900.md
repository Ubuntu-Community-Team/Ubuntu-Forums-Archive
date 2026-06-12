---
title: "A8V-VM SE integrated Gfx 1440x900"
date: 2008-02-24
forum: Absolute Beginner Talk
---

### Post by 1inxs on 2008-02-24
I tried to install Ubuntu 5.04 back inn 2005, but failed on my PC. I now built a new system and have installed Ubuntu 6.06 LTS. The following lists a little about my new system.  

Asus A8V-VM SE with Integrated Gfx Integrated in North Bridge onboard graphics. Northbridge chip is a VIA K8M890. My monitor is an Acer AL1916W. I need help in getting my native resolution of 1440x900 working.

Section "Device"
	Identifier	"Generic Video Card"
	Driver		"vesa"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"AL1916W"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Generic Video Card"
	Monitor		"AL1916W"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1440x1440" "1280x1024" "1280x960" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1440x1440" "1280x1024" "1280x960" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1440x1440" "1280x1024" "1280x960" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1440x1440" "1280x1024" "1280x960" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1440x1440" "1280x1024" "1280x960" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1440x1440" "1280x1024" "1280x960" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus" "SendCoreEvents"
	InputDevice     "cursor" "SendCoreEvents"
	InputDevice     "eraser" "SendCoreEvents"
EndSection


Could I please get help? Thanks in advance.

---

### Post by incen on 2008-02-24
I checked this board for you. However, I could only find their support for Windows system:
[http://support.asus.com/download/download.aspx?modelname=A8V-VM%20SE&SLanguage=en-us](http://support.asus.com/download/download.aspx?modelname=A8V-VM%20SE&SLanguage=en-us)

Could you just add in "1440x990" in your xorg.cof and try if it works?

---

### Post by 1inxs on 2008-02-24
I have added "1440x900" to my xorg.conf. How do I save and exit Gedit?

---

### Post by incen on 2008-02-24
You can either do it with Ctrl+S (as under Windows) or click on the forth icon, saying "save the current file", on the gedit panel. :)

---

### Post by 1inxs on 2008-02-24
Incen,
 :oops: In the past I used vim. This is my first time using Gedit. I guess I figured it would be more difficult to use. I'm so used to always seeing icons in the MS XP window. Gedit is a super user friendly editor. Thanks for all the help. I now run my monitor at 1440x900 resolution. To sum up what I did to get it fixed and running. In a terminal
  (1) sudo gedit /etc/X11/xorg.conf
  (2) added "1440x900" on each resolution line
  (3) clicked on the save icon
  (4) did ctrl + Alt + Backspace to restart
  (5) System Preferences Screen Resolution and clicked on the screen resolution. Scrolled up to 1440x900 Apply and it has a beautiful 1440x900 desktop. I hope this helps somebody else with res problems.

---

### Post by incen on 2008-02-25
Great that it helped you! ^^
Yeah~ gedit is terribly user friendly... :P
By the way, if this solved your problem, you should mark your thread as 'solved' as you might be reminded with a private message. HA!
Anyway, to do so, go to Thread Tool -> Mark this thread as solved'. ^^

---

