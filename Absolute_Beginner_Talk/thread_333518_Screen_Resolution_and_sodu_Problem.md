---
title: "Screen Resolution and sodu Problem"
date: 2007-01-07
forum: Absolute Beginner Talk
---

### Post by andstuff on 2007-01-07
Hi, I'm a total noob to Linux in general. I just instal Ubuntu on my computer and I'm having trouble with the screen resolution and SODU.

For my screen resolution, I'm stuck at 640x480. I tried all kinds of stuff in the terminal from this forum, it seems that I have ubu recognizes my screen and graphic controler, it says all the different all the resolutions possible in a text document, but I can't choose them in "Screen Resolution Preferences"

And for my sodu problem, whenever I type sodu in the terminal, it asks me a password, I type in the only password I have given associated to ubu [my user, the password works elsewhere in ubu, like in administration stuff] and it says that it's the wrong password...

Any help would be appreciated :-k

---

### Post by jvc26 on 2007-01-07
Do you mean 'sudo'? If so the password it asks for will be the one you use for user and for all admin tasks. It appears odd that that doesnt work.
Il

---

### Post by andstuff on 2007-01-07
> **Illuvator said:**
> Do you mean 'sudo'? If so the password it asks for will be the one you use for user and for all admin tasks. It appears odd that that doesnt work.
Il
Yes I ment sudo... haha

---

### Post by andstuff on 2007-01-07
Okay I got the sudo thing worked out ! :)  If someone could help me with my screen resolution, it would really be appreciated!

I guess some info would be necesary...

> Section "Device"
	Identifier	"Intel Corporation 82915G/GV/910GL Express Chipset Family Graphics Controller"
	Driver		"i810"
	BusID		"PCI:0:2:0"
EndSection

Section "Monitor"
	Identifier	"1772ED"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation 82915G/GV/910GL Express Chipset Family Graphics Controller"
	Monitor		"1772ED"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480" "1x1" - Copied from xorg.conf

Even though I got it copied from a linux file, it doesn't mean I know what I'm doing :rolleyes:

---

### Post by MkfIbK7a on 2007-01-07
so whats rong with your resolution?

---

### Post by MkfIbK7a on 2007-01-07
do
> sudo dpkg-reconfigure xserver-xorg 
in a terminal
 answer the quuestions correctly
 when it asks for a resolution choose only the correct one 
(e.g. 1280x 1024 only deselect all others by the way you use space bar to select and deselect)
next when it  asks "simple medium advanced"
 choose simple and choose your monitor size 
finish answering the questions then press
ctrl+alt+backspace to reset the x server 
hope this helps

---

### Post by andstuff on 2007-01-07
Thanks, it didn't work actualy, but since it screwed eveerything up, I had to reinstall so while reinstalling I went in "safe graphic mode" just to try it, and it works !

Thanks guys :)

Ps: this might have to go in FAQs somewhere, I think there are alot of "screen resolution" threads on this forum...

---

### Post by alienexplorers on 2007-01-07
To change the video mode to the one you are wanting to run go to this page:
[http://www.sh.nu/nvidia/gtf.php](http://www.sh.nu/nvidia/gtf.php)

You then input you Vert & Horz&refresh rates and it generates a Modeline.
Example if you want to run 1024*768*75 the modeline would be:
Modeline "1024x768_75.00"  81.80  1024 1080 1192 1360  768 769 772 802  -HSync +Vsync

This line would be added to your xorg.conf as so:
Section "Monitor"
Identifier "1772ED"
Option "DPMS"
Modeline "1024x768_75.00"  81.80  1024 1080 1192 1360  768 769 772 802  -HSync +Vsync
EndSection

Hope this helps.

---

### Post by Android8675 on 2007-01-16
.

---

### Post by ljpm on 2007-01-16
I had the same problem with screen resolution. What worked for me was running

```
sudo dpkg-reconfigure xserver-xorg 
```

and entering the correct hscan and vscan ranges for my monitor. It seems that if xorg.conf has no, or incorrect, hscan and vscan ranges then it prevents resolutions higher than 640x480 which I assume is to protect the monitor.

---

