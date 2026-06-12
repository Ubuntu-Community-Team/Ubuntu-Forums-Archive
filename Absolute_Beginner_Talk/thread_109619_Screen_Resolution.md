---
title: "Screen Resolution"
date: 2005-12-29
forum: Absolute Beginner Talk
---

### Post by noob_Lance on 2005-12-29
Hey, Im trying to get my new lcd screen to work right with linix... and i have tried to reconfigure my x-server 2 times... once on manual and once on auto detect.. both times... it died and killed X when trying to auto detect my external monitor... i have also tried editing the /etc/X11/xorg.conf 5 times... 4 times in the command line because x crashed every time i tried to change it.. until i restored it..

Can ANYONE Please Help me with this problem..

Thank You
~Lance

---

### Post by rjwood on 2005-12-29
Rather than auto detect-you can input the info from your manual. That is what I did. Worked fine for me.Good Luck!

---

### Post by noob_Lance on 2005-12-29
input it where? thats what i cant figure out... i was told to try in the xorg.conf... but theres somethin already there about it... how can i switch from this to the monitor so i can get a better res??


*edit* i see 20 different modes in my manual..

---

### Post by Perfect Storm on 2005-12-29
[http://ubuntuforums.org/showthread.php?t=107067](http://ubuntuforums.org/showthread.php?t=107067) see if there any helps in this post.

---

### Post by noob_Lance on 2005-12-29
that didnt help really... heres the section that includes my external monitor

```

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	Modeline	"1280x800@60" 83.91 1280 1312 1624 1656 800 816 824 841
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation 82852/855GM Integrated Graphics Device"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x800"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice	"Synaptics Touchpad"
EndSection

```

---

### Post by anil_robo on 2005-12-29
I tried to autoconfigure xserver while it was still running. It crashed consistently. SO I did a little workaround.

I rebooted the machine in recovery mode from GRUB boot options, and clicked the SESSION button. Then I chose the last option "failsafe terminal" and entered username and password to logon.

A little terminal was sitting prettily in the lower right corner of screen. There I was able to reconfigure x ```
sudo dpkg-reconfigure xserver-xorg
```.

It did take me 2-3 tries, but finally I was able to get back the good resolution for my laptop screen! If I can do it, anyone can do it! :)

---

### Post by noob_Lance on 2005-12-29
alright the screen Res works now... but now.. my external hard drive dosnt show up... and when i log in... i get 2 errors


```

Internal error

failed to initialize HAL!

```

and second error

```

Can't access ACPI events in /var/run/acpid.socket! Make sure the ACPI subsystem is working and the acpid daemon is running.

```

---

### Post by noob_Lance on 2005-12-29
haha.... moron here *ME* was still in recovery... i didnt reboot HAHA! im a moron lol

---

### Post by Perfect Storm on 2005-12-29
Nice to see you solved the problem ^^

---

### Post by noob_Lance on 2005-12-29
it sure it a sight for sore eyes... Thanks Everyone for your help... :)

---

