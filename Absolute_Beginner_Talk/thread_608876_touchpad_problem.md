---
title: "touchpad problem"
date: 2007-11-10
forum: Absolute Beginner Talk
---

### Post by inter-m on 2007-11-10
hi...
Im trying to start the touchpad gui control from System>> Prefrences>> Touchpad... For some reason it shows this error...

GSynaptics couldn't initialize.
You have to se 'SHMConfing' true' in xorg.conf or XF8Config to use GSynaptics

please help...:confused:

---

### Post by Harpoon on 2007-11-10
You need to do a little bit of editing:
First, I'd suggest you get into a terminal and get into the correct directory:
cd /etc/X11

then make a backup of the file you will be editing:
sudo cp xorg.conf xorg.conf.backup

Then, open the file in a text editor as root.  I use
sudo gedit /etc/X11/xorg.conf

Once thisis displayed, look for the section that looks like this:

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"	"/dev/psaux"
	Option		"Protocol"	"auto-dev"
	Option		"HorizScrollDelta"	"0"
	Option		"SHMConfig"       "on"
EndSection

Using copy/paste you can add the SHMCongig line just as it is shown above.

I don't remember if you need to restart the gnome, but if you do you can just press <Control> <Alt><Backspace> and you can log back in without rebooting.

This should solve your problem.

if you want to turn the touchpad off, then
sudo synclient touchpadoff=1;  
to turn it back on,
sudo synclient touchpadoff=0.

You won't get any response on the screen, so just try the touchpad to see if it is acting the way you want.

BTW, the on/off commands only hold till the next time you restart.

---

