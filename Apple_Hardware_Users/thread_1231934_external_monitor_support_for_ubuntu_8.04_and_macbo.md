---
title: "external monitor support for ubuntu 8.04 and macbook 3,1 (santa rosa)"
date: 2009-08-05
forum: Apple Hardware Users
---

### Post by rifak on 2009-08-05
hey everyone,
i am running 8.04 with a macbook 3,1 (late 2007 model) and am wondering if anyone has gotten an external monitor working. i have an LG Flatron and using the mini-dvi to vga adapter. i dont care about running compiz or any effects because i have them always turned off. i would even be fine with just a simple cloned output at native resolution of the external monitor (which is 1440x900). any input or ANYTHING would be awesome..ive been trying everything but nothing has worked.

---

### Post by rifak on 2009-08-06
alright, so here it is. i have searched and searched for the last couple days on how to get this done, but I have not come across a definitive solution that works for a Black Macbook Santa Rosa running Ubuntu 8.04, BUT i have figured it out and it works like a charm. so here it is.

i have a black macbook 3,1 (santa rosa) with an intel x3100 graphics card with a mini-dvi outport. my monitor is a VGA monitor, so i have the mini-dvi to vga adapter connecting. the external monitor is an LG flatron 1440x900 widescreen res.

first, unplug the external, disable compiz and all effects, and restart (if it wasn't plugged in, then dont worry about it)

i first edited the xorg.conf to look like this (this is just the relevant part for the screens and monitors and what not...so only change the parts of the xorg.conf that i have shown here)

```

Section "Device"
	Identifier	"Configured Video Device"
	Driver          "intel"
	Option          "monitor-LVDS"    "laptop"
	Option          "monitor-TMDS-1"  "external"
EndSection

Section "Monitor"
	Identifier	"laptop"
	Option "PreferredMode"  "1280x800"
EndSection

Section "Monitor"
	Identifier      "external"
	Option          "RightOf"   "laptop"
	Option "PreferredMode"  "1440x900"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation 945G Integrated Graphics Controller"
	Monitor		"laptop"
	SubSection "Display"
		Depth  24
		Modes  "1440x900" "1280x800"
		Virtual	2720	900
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier    "Default Layout"
	Screen        "Default Screen"
	InputDevice    "Synaptics Touchpad"
EndSection

```

so what this is saying (from top to bottom) is that i am using the intel driver, with options of the monitors that i have. LVDS is your laptop monitor, while TMDS-1 is for the dvi port. i then define my laptop monitor and external monitor in separate monitor sections, with the options of preferred resoultions (you can change these to match your monitors). i then define the Screen section. here, i make one big screen with a virtual res of 2720x900 (this can be done by adding your external and laptop monitors. if they are side by side, then: 1280+1440=2720 and 800+900=900. if they are above or below, then: 1280+1440=1440 and 800+900=1700). make sure to add the modes subsection with the resolution of both external and laptop monitors. alright, now logout and log back in.

plug your external monitor in and run the following command:

```

gtf 1440 900 60

```

this will output some text, and just copy paste the Modeline to the xrandr --newmode command (my Modeline read "1440x900_60.00" 106.47 1440 ....

then start the xrandr commands, with, like i said, the Modeline output replaced in the first command. 

```

xrandr --newmode "1440x900_60.00" 106.47 1440 1520 1672 1904 900 901 904 932 -HSync +VSync

xrandr --addmode VGA 1440x900_60.00

xrandr --output VGA --mode 1440x900_60.00

xrandr --output VGA --right-of LVDS

```

one note, if your external monitor is not a VGA, but is a DVI, then I am pretty sure you just need to replace the VGA with TMDS-1 (althought im not sure, i dont have a dvi screen to test on).

after all said and done, you should have an extended desktop to the right with full res on both screens. if not, try to do a restart with the external plugged in the whole time...if it still doesn't work, post back here and ask.

remember, you will need to disable compiz for this (i dont use it anyways, so its not a problem for me).

after doing this and restarting and testing everything to see if this method can break, I have not found any situation where this doesnt work. in general, you will want to start your computer without the monitor plugged in, log in, plug it in, then run the commands. like i said, if that doesnt work, try and restart and maybe some different combos or plugging in and unplugging, but dont change the text or commands, those are fine.

one last thing. after doing this, firefox had a problem with history remembering or something. i dont know if what i did caused it (to be honest, i have no clue why in the world what i was doing would have done that) but if that happens to anyone, post here an ill tell you how i fixed it. if youre reading this, dont be afraid of this, because it probably was not this that caused it..but if it is, its an easy fix.

---

