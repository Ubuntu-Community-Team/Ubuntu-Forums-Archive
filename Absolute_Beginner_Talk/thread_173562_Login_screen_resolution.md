---
title: "Login screen resolution?"
date: 2006-05-10
forum: Absolute Beginner Talk
---

### Post by shurguywutt on 2006-05-10
When I log in to Ubuntu, a box keeps coming up and floating around on my monitor, saying "Input not supported"  Is there any way I can change the resolution of the login screen?  It used to do the same thing on the Ubuntu desktop.  Until I changed the resolution.  I am guessing i need to do the same thing to the login screen, but i dont know how.  Can anyone help me?

---

### Post by Omnios on 2006-05-10
Its a good idea to make a backup. sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup

Try in terminal sudo gedit /etc/X11/xorg.conf or in command line sudo nano sudo gedit /etc/X11/xorg.conf. Nano is a command line text editor. This is your xorg config file and what you are looking for is screen resalutions neer the bottom.
```
Section "Monitor"
	Identifier	"A91f+"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NV18 [GeForce4 MX 4000 AGP 8x]"
	Monitor		"A91f+"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1792x1344" "1600x1200" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1792x1344" "1600x1200" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1792x1344" "1600x1200" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1792x1344" "1600x1200" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1792x1344" "1600x1200" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1792x1344" "1600x1200" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
EndSection
```

 Now xorg tryes running the highest resalution it can before you actualy get into your GUI where it defaults to the set resalution what you want to do here is remove the resalutions you do not want as they will no longer be available in gnome screen resalution settings. For example.

 ```
SubSection "Display"
		Depth		24
		Modes		"1792x1344" "1600x1200" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
```

 In this one I would remove the "1792x1344" entry as I do not use it, hopefully you get the idea. Also the Depth is the color depth which is why you have all those res entries. 
Good Luck.

---

### Post by deanjm1963 on 2006-05-10
I had a similar problem, I like my monitor resolution at 1400x1050, but for the login screen it defaulted back to 1600x1200. A quick and easy fix was to edit my xorg.conf and search for "1600x1200" and replace it with "1400x1050", save it, and restart X.

It's a good idea to make a backup copy of your xorg.conf file first.

open a terminal and type

sudo gedit /etc/X11/xorg.conf

make your changes and save.

exit and reboot.

---

### Post by DA_uf on 2006-05-10
Check out /etc/x11/xorg.conf and also the man pages **man xorg.conf**
You probably need to change the resolution to one your monitor supports.

D'oh..3rd on the 1 minute draw.  Above has more thorough answers anyway.

---

### Post by Monster_user on 2006-05-10
GDM automatically runs at the highest resolution support by your system. Foolishly in my Opinion.

1. With newer system that support ultra high resolutions, the text can get too small to be readable.

2. Sometimes the highest settings are incorrectly detected, and a box that says "Input not supported" shows up.

You will need to edit the '/etc/X11/xorg.conf' file. Lowering the maximum resolution.

Press Alt-F2 to open a Run dialog box, and then copy and paste the following.

> gksu gedit /etc/X11/xorg.conf

Then scroll about halfway down. You should see a section called "Screen. Delete the higher resolution settings.

> Section "Monitor"
	Identifier	"StdioDsply17"
	Option		"DPMS"
	VertRefresh	47-160
	HorizSync	30-85
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Device1"
	Monitor		"StdioDsply17"
	DefaultDepth	24
	SubSection "Display"
		Depth		16
		Modes		"1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

You notice where mine says it says,...

Depth		16
Modes		"1152x864" "1024x768" "800x600" "640x480"

Delete the first resoultion, save, and then reboot. Repeat untill this works. You may also need to delete it for the 24-bit depth resolution as well. Depending on what your default depth is.

Depth		24
Modes		"1152x864" "1024x768" "800x600" "640x480"

> Section "Monitor"
	Identifier	"StdioDsply17"
	Option		"DPMS"
	VertRefresh	47-160
	HorizSync	30-85
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Device1"
	Monitor		"StdioDsply17"
	DefaultDepth	24
	SubSection "Display"
		Depth		16
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
EndSection

----------------------------------------------------------------------------------------------------------------------------------------

Alternatively, you could reorder the resolutions. So that a smaller resolution is first. Such as "800x600".
[http://lists.debian.org/debian-user/2004/12/msg01208.html](http://lists.debian.org/debian-user/2004/12/msg01208.html)

Depth		16
Modes		"800x600" "1152x864" "1024x768" "640x480"

Then add the following to the end of '/etc/gdm/gdm.conf'.

SetPosition=true
PositionX=130
PositionY=110

I am running Ubuntu 6.10, Dapper Drake, so there may be some differences

Alt-F2 and paste the following

> gksu gedit /etc/gdm/gdm.conf

Then press "Ctrl-F" or select "Search -> Find", and search for "SetPosition".

When you find it, change "SetPosition" to true, and "uncomment it" (which means to delete the "#" symbol in front of the line).

> # offset from the right or bottom edge.
#SetPosition=false
#PositionX=0
#PositionY=0

> # offset from the right or bottom edge.
SetPosition=true
PositionX=130
PositionY=110

---

### Post by shurguywutt on 2006-05-10
okay ive gone through basically all of this and it still is happening, even when i put it on 800x600 i still get the message "input not supported"  Something i thought that was strange was on the screen resolution selection page, the higher resolutions will work, as long as i set the hertz level to a lower level.  is there anyway i can change the hertz level for the login screen?  
thanks

---

### Post by Monster_user on 2006-05-10
Yes, but finding the information is difficult.

You have to get out the Monitor's manual, or browse through all the Menu options on the Monitor.

On my 17' Apple Studio Display CRT, it actually lists the supported resolutions, when that box shows up.

Input out of Range.
Supported resoltuions
Vertical 47hz to 160hz
Horizontal 30hz to 85hz.

> Section "Monitor"
Identifier "StdioDsply17"
Option "DPMS"
VertRefresh 47-160
HorizSync 30-85
EndSection

The section you want to change, is the VertRefresh, and HorizSync.

Try setting the HorizSync to 30-85, and the Vertical refresh to 47-60.

> Section "Monitor"
...
VertRefresh 47-60
HorizSync 30-85
EndSection

---

