---
title: "Problem with Restricted Driver for nVidia 7600GT"
date: 2008-03-27
forum: Absolute Beginner Talk
---

### Post by emptybox on 2008-03-27
A newbie needing some help.

I just installed an nVidia 7600GT card on my system (Ubuntu 7.10).
I managed to get it going  by using the nv drivers, and it works fine, but obviously won't allow me to select the desktop effects.

I installed the nvidia-glx-new driver through Restricted Drivers, and it allows me to set the desktop effects, but it gives me a weird diagonal interference-like pattern on the screen.
It's quite faint, and seems to come in waves, but is annoying.
Has anybody had similar problems with this card and driver, and is there any way to solve it?

I'm pretty sure it's this driver that's causing it, because if uninstall the driver and go back to using the nv driver, then the problem goes away.

I looked on the nVidia site to see if they had any better drivers, and downloaded
NVIDIA-Linux-x86-169.12.pkg1.run, but I can't work out how to install it and get it working?

Using the command "sh NVIDIA-Linux-x86-169.12.pkg1.run" doesn't seem to have any effect in a terminal, and when I tried it through Recovery Mode it said it couldn't open the file?

I've heard people talk about opening a shell by doing Ctrl-Alt-F1, but when I tried that all I got was a black screen with a winking cursor top right, but it wouldn't take any input, and I had to either restart or Ctrl-Alt-F7 to get back to the gui?

By the way, the relevant bits of my xorg.conf are - 
......................................................
Section "Device"
	Identifier	"Generic Video Card"
	Driver		"nvidia"
	Busid		"PCI:1:0:0"
	Option		"AddARGBVisuals"	"True"
	Option		"AddARGBGLXVisuals"	"True"
	Option		"NoLogo"	"True"
EndSection

Section "Monitor"
	Identifier	"W24OD D-Sub"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Generic Video Card"
	Monitor		"W24OD D-Sub"
	Defaultdepth	24
	SubSection "Display"
		Modes		"1920x1920"	"1920x1200"	"1680x1680"	"1600x1200"	"1280x1024"	"1280x960"	"1152x864"	"1024x768"	"832x624"	"800x600"	"720x400"	"640x480"
	EndSubSection
EndSection
...............................................................

I notice it just says "Generic Video Card" rather than identifying the card, but it is correctly identified in nvidia-settings.

Apologies for such a long first post. :)

---

### Post by wolfen69 on 2008-03-27
i had major problems with my 7300GS with feisty and gutsy. that is, up until i tried Hardy beta. Compiz works flawlessly for the first time. i don't have a fix for you, but all i can say is try Hardy out and see what happens. if you dont trust the beta, it's less than a month until the final release comes out.

---

### Post by forrestcupp on 2008-03-27
Just install [Envy](http://www.albertomilone.com/nvidia_scripts1.html) and let it do it all for you automatically.

As new as you are, I'd use Envy before trying Hardy beta.

---

### Post by thisismalhotra on 2008-03-27
> **forrestcupp said:**
> Just install [Envy](http://www.albertomilone.com/nvidia_scripts1.html) and let it do it all for you automatically.

As new as you are, I'd use Envy before trying Hardy beta.

I second this way to go..

---

### Post by emptybox on 2008-03-27
Thanks for the responses, and the advice. :)

I downloaded Envy and let it do it's thing, after uninstalling the restricted driver.

However I am still getting these interference patterns on the screen.
They are faint and shimmery diagonal lines across the screen. Sometimes they disappear and then reappear after a few seconds.

I'm begining to think it may be the graphics card (it was second hand), although there is no problem using the nv drivers, and the problem only starts when you get to the logon screen? :confused:

Actually, I just tried an experiment.
The monitor is a 24" 1920x1200.
I tried lowering the resolution to 1280x768, and lo and behold the interference went away.
Even after I reset it to 1920x1200, it hasn't returned as yet. :)

So I don't know what i have done, but it seems to be solved at the moment.
Perhaps the driver struggles at that resolution?

---

