---
title: "Help with TV-Out"
date: 2006-12-31
forum: Absolute Beginner Talk
---

### Post by MrJackdaw on 2006-12-31
Hi!
Yes, I am a comp lete newbie to Linux and am feeling, well, a little overwhelmed!

Before I make the complete change to Ubuntu I need to ensure my Dell Inspiron 6000 Laptop can do a few things, many of which I have sorted myself.

One I can't :-k 

How can I get the TV-Out working? It just doesn't show up as an option in Totem - all greyed out!


(Sorry if posted in wrong section)


James

---

### Post by Jeff24K on 2006-12-31
You might want to start here....

[http://www.ubuntuforums.org/showthread.php?t=98456](http://www.ubuntuforums.org/showthread.php?t=98456)

---

### Post by tagra123 on 2006-12-31
The how to above will work, but I found that the atitvout  will work without all the messing in the conf files.  I do recall needing to make sure that the driver was set to vesa. An somewhere I read that the resolution needs to be 800 X 600, but I seem to remember have a higher resolution than that.


 atitvout is in the universe repository,  

use
[B]apt-get install atitvout.
[/B]
Some info about atitvout 

[http://www.die.net/doc/linux/man/man8/atitvout.8.html](http://www.die.net/doc/linux/man/man8/atitvout.8.html)

For it to work correctly make sure to specify ntsc or pal

The s-video cord nees plugged in before booting for ubuntu to recognize the device,.

remember to use sudo

[B]sudo atitvout -f t     for tv
sudo atitvout -f l     for lcd

sudo atitvout -detect[/B]

---

### Post by MrJackdaw on 2007-01-01
Well, tagra123, your idea sounded easiest, but it didn't work with my intel on-board graphics :( Thanks very much for your assist though!

Thanks anyway! Now, lets try the other route :)

Just looked at link, and that's only for NVidia cards... Blast!

---

### Post by tagra123 on 2007-01-01
I have this working on a Dell 3800

What did you get when you tried sudo  atitvout -detect  ?


Did you try

sudo atitvout ntsc -f t

Try changing the driver to vesa in /etc/X11/xorg.conf

make a backup of the original xorg.conf file

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.original

edit it
sudo gedit /etc/X11/xorg.conf

look for this section

Section "Device"
	Identifier	"ATI Technologies, Inc. Rage 128 PF/PRO AGP 4x TMDS"
	Driver		"ati"

Change Driver  "ati"                to                 Driver "vesa"

Save the file.

reboot

if for some reason you display wont show correctly you can undo this change from arescue terminal by typing

sudo rm /etc/X11/xorg.conf
sudo cp /etc/X11/xorg.conf.original /etc/X11/xorg.conf


and rebooting.

---

### Post by MrJackdaw on 2007-01-01
I have _nearly_ resolved this using by editing Xorg.conf and pasting in a load of stuff I didn't understand :)

The result is a two-monitor setup that works extremely well! :)

Is it proper for me to post the code?

And thank you again for the assistance!

---

### Post by tagra123 on 2007-01-01
Post it.  -- it may help someone in the future.

I booted up my laptop and remembered at that point that I had Xubuntu. I'll bet I edited the xorg.conf and just forgot. It was over 6 months ago.

---

### Post by MrJackdaw on 2007-01-03
Ok here is the text of my xorg.conf - 

*Only reproduced from the Device section onwards!*

```
#Beginning of monitor preferences...

Section "Device"
	Identifier	"Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller"
	Driver		"i810"
	BusID		"PCI:0:2:0"
EndSection

Section "Device"
	Identifier "LCD_CRT"
	Driver "i810"
	Option "MonitorLayout" "CRT,LFP"
	Screen 0
	BusId "PCI:0:2:0"
EndSection

Section "Device"
	Identifier "CRT"
	Driver "i810"
	Option "MonitorLayout" "CRT,LFP"
	Screen 1
	BusId "PCI:0:2:0"
EndSection

Section "Device"
	Identifier "LCD_TV"
	Driver "i810"
	Option "MonitorLayout" "TV,LFP"
	Screen 0
	BusId "PCI:0:2:0"
EndSection

Section "Device"
	Identifier "TV"
	Driver "i810"
	Option "MonitorLayout" "TV,LFP"
	Option "TVStandard" "PAL-M"
	Option "TVOutFormat" "SVIDEO" # "Composite" or "SVIDEO" or "RBG"
	Option "ConnectedMonitor" "TV" 
	Screen 1
	BusId "PCI:0:2:0"
EndSection

Section "Monitor"
	Identifier	"LCD"
	Option		"DPMS"
	Modeline	"1280x800@60" 83.91 1280 1312 1624 1656 800 816 824 841
EndSection

Section "Monitor"
	Identifier	"CRT"
	Option		"DPMS"
EndSection

Section "Monitor"
	Identifier "TV"
	HorizSync	30-50
	VertRefresh 60
EndSection


Section "Screen"
	Identifier	"LCD_CRT"
	Device		"LCD_CRT"
	Monitor		"LCD"
	DefaultDepth	24
	SubSection "Display"
		Depth		16
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x800"
	EndSubSection
EndSection

Section "Screen"
	Identifier	"LCD_TV"
	Device		"LCD_TV"
	Monitor		"LCD"
	DefaultDepth	24
	Subsection "Display"
		Depth		16
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x800"
	EndSubSection
EndSection

Section "Screen"
	Identifier "CRT"
	Device "CRT"
	Monitor "CRT"
	DefaultDepth 24
	Subsection "Display"
		Depth 24
		Modes "1024x768"
	EndSubsection
EndSection

Section "Screen"
	Identifier "TV"
	Device "TV"
	Monitor "TV"
	DefaultDepth 24
	Subsection "Display"
		Depth 24
		Modes "1024x768" "800x600"
	EndSubsection
EndSection

Section "ServerLayout"
	Identifier "LCDandTV"
	Screen 0 "LCD_TV"
	Screen 1 "TV" RightOf "LCD_TV"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus" "SendCoreEvents"
	InputDevice     "cursor" "SendCoreEvents"
	InputDevice     "eraser" "SendCoreEvents"
	InputDevice	"Synaptics Touchpad"
EndSection

Section "ServerLayout"
	Identifier "LCDandCRT"
	Screen 0 "LCD_CRT"
	Screen 1 "CRT" RightOf "LCD_CRT"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus" "SendCoreEvents"
	InputDevice     "cursor" "SendCoreEvents"
	InputDevice     "eraser" "SendCoreEvents"
	InputDevice	"Synaptics Touchpad"
EndSection

Section "ServerLayout"
	Identifier "LCDOnly"
	Screen 0 "LCD_CRT"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus" "SendCoreEvents"
	InputDevice     "cursor" "SendCoreEvents"
	InputDevice     "eraser" "SendCoreEvents"
	InputDevice	"Synaptics Touchpad"
EndSection
	
Section "ServerFlags"
#	Xinerama support gives a single big monitor!
# 	Option "xinerama" "true"
	Option "DefaultServerLayout" "LCDandTV"
#	Option "DefaultServerLayout" "LCDandCRT"
#	Option "DefaultServerLayout" "LCDOnly"
EndSection

Section "DRI"
	Mode	0666
EndSection
```

You simply un # the section in ServerFlags that you want and ctrl-alt-backspace to reboot the GUI.

Bit of a pain when I want to change, but that's OK.

May change with the new Xorg huh?

---

### Post by MrJackdaw on 2007-01-17
Update: Does not work well with Data Projector. Trying new ideas...

Solved: Just had to edit Xorg and put in more modes for the monitor...

---

