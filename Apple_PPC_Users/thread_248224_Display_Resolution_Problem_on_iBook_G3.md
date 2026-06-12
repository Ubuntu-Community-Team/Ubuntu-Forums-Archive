---
title: "Display Resolution Problem on iBook G3"
date: 2006-08-31
forum: Apple PPC Users
---

### Post by Ken4759 on 2006-08-31
Hi, I'm new to this forum and new to linux. I am using an old g3 iBook with Xubuntu loaded on it. Why I chose that particular version is because ubuntu 6.06.1 wouldn't get past picking the language screen.

My iBook is a 600 G3 with 20g HD and 256m of ram. The problem I'm having is the display resolution default is apparently 640x480 and the only option listed is 320x240. The menu bar and the task bar are very large. When I open some of the programs, the bottom of the window is behind the taskbar covering up some of the buttons.

I'm really used to using 1024x768 and at a minimum 800x600 which is the default resolution for this iBook.

Is there a way to get higher resolutions or maybe fix the large menubar and taskbar? The answer to this will determine whether I keep using xubuntu or go back to OSX on this computer.

Thanks in advanced for any help.

Ken

---

### Post by meyerfun on 2006-09-20
Did you ever resolve this issue.  I am having the same problem, and I cannot find any clues to changing the resolution.

TIA

jm

---

### Post by Chain-Q on 2006-09-20
Although i'm using Ubuntu, and not Xubuntu on my iBook G3/600, it works flawlessly at 1024x768/16 bits, using the Rage Mobility M3 chip inside. (Actually, it works using 24 bits too, but that means disabled direct rendering, due to the limited video memory of this machine (8MB only).)

Posting contents of /etc/X11/xorg.conf, and /var/log/Xorg.0.log files for examination could allow me to give you further hints... Also output of "sudo cat /proc/cpuinfo" and "sudo lshw -C display" might give more help.

---

### Post by edkroket on 2006-09-21
In Terminal
sudo gedit /etc/X11/xorg.conf
scroll down to this section and ad your reslolution in this way;
Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies, Inc. Radeon RV250 If [Radeon 9000 Pro]"
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
Save it and restart.

---

### Post by stmiller on 2006-09-21
I really doubt an iBook G3 can do 1280x1024 resolution. I would take out all of those mentionings.

You just need one line that says this:

Depth 24
Modes "1024x768" "800x600" "640x480"

---

