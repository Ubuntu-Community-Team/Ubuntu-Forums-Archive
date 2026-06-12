---
title: "What's needed for visual effects?"
date: 2007-11-20
forum: Absolute Beginner Talk
---

### Post by Fayte2071 on 2007-11-20
Hey all. I just bought a new laptop. a sony vaio VGN-FX240e and installed ubuntu and all that. But now I can't activate the visual effects. What exactly do i need for it? A geforce or ATI? I have an integrated video card, is there anyway i can get that to work with the effects?

---

### Post by AlexenderReez on 2007-11-20
check your graphic -->

>  lspci | grep VGA
sudo nvidia-xconfig --add-argb-glx-visuals

---

### Post by Fayte2071 on 2007-11-20
Sadly, it's giving me an error....
nvidia-xconfig: unrecognized option: "--add-argb-glx-visuals"

Invalid commandline, please run `nvidia-xconfig --help` for usage information.

---

### Post by Inxsible on 2007-11-20
please post the output of ```
lspci | grep VGA
```

---

### Post by Fayte2071 on 2007-11-21
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)

---

### Post by jordanmthomas on 2007-11-21
You shouldn't need to do anything special with that chip to get compiz running.
What's in your /etc/X11/xorg.conf ?

Specifically, I am wanting to see if you are using the intel driver.

---

### Post by Fayte2071 on 2007-11-21
:\ I'm not sure what's in my xorg...sorry i'm relatively new to ubuntu, where do i go to tell you what you need?

---

### Post by jordanmthomas on 2007-11-21
press alt + f2 and type this:
```
gedit /etc/X11/xorg.conf
```
and copy and paste what's in there.

(just as a note, if you end up having to edit this file change that to 
```
gksudo gedit /etc/X11/xorg.conf
``` so you will have permission)

---

### Post by Fayte2071 on 2007-11-21
K, i'm assuming you want to know just about the graphics card, so here it is..

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"cursor"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller"
	Driver		"intel"
	BusID		"PCI:0:2:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	30-70
	VertRefresh	50-160
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller"
	Monitor		"Generic Monitor"
	DefaultDepth	24
EndSection

---

### Post by jordanmthomas on 2007-11-21
OK, this seems to be in order.
However, it seems I was a bit hasty in assuming your card will work in compiz easily.
[http://wiki.compiz-fusion.org/Hardware/Blacklist](http://wiki.compiz-fusion.org/Hardware/Blacklist)

It appears it is blacklisted for now (it should still work though, except video might be messed up sometimes)
According to the link, running this in a terminal should allow you to start compiz
```
SKIP_CHECKS=yes compiz-manager
```

---

### Post by Fayte2071 on 2007-11-21
Alright, that didn't work.. but i did skip_checks=yes compiz and that worked...but it seems i have to leave the terminal on and i can't use it

---

### Post by jordanmthomas on 2007-11-21
you  can do this to gain back your terminal (and be able to use it)
first, hit ctrl-c to kill compiz.  Then,
```
skip_checks=yes compiz &
```
Then, either hit ctrl-d or type exit and hit enter (but don't just close the window with the button or compiz will die).

---

### Post by Fayte2071 on 2007-11-21
? Sorry i'm a tad confused, and i apologize if i'm just wasting your time...when i kill compiz, then i type that in and get
[1] 8452
g@Katamari:~$ Checking for Xgl: not present. 
Blacklisted PCIID '8086:2a02' found 
aborting and using fallback: /usr/bin/metacity

---

### Post by jordanmthomas on 2007-11-21
Yes, now either type exit and hit enter or press ctrl-d

What you did by putting & at the end of the compiz comand was to separate it from the terminal process.  It keeps running and gives you your prompt back.  Its output still goes to the terminal, so it LOOKS unusable, but you are able to type commands and use it still.

**edit**
woops, it looks like compiz isn't running now.  It's weird that it says it's blacklisted and then quits because you told it to skip checks.
I'm not sure what's wrong here.

---

