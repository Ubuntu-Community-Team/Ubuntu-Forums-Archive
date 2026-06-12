---
title: "[SOLVED] No love for my Radeon 9250"
date: 2008-01-14
forum: Absolute Beginner Talk
---

### Post by Colin The New Guy on 2008-01-14
Hello all!

I decided this weekend past to finally see what all the buzz was surrounding Ubuntu, so I've downloaded and installed a copy of 7.10 for my 64 system.  So far, I'm really liking what I've seen, particularly the level of community involvement.  You people are awesome.

In any case, I was hoping I could get some help with this issue.  I'm running a Radeon 9250  video card, and after some initial difficulty installing surrounding my display, I've been through the forums to see about a driver to make my video card work properly.  Currently I have to have visual effects off, and anything 3D makes my system slow to an absolute crawl, which is really sad because I'd love to be able to employ a few effects... and maybe a reasonable screen resolution.

I've done some homework;  I've followed a few suggestions from other threads without success, the final one I tried involved using a program called "Envy" which automated downloading of drivers and installing them from the ATI website.  I had hoped that my problem was solved, but in the end I received a message that there is no support for the Radeon 9250 on this version of the OS.

With that in mind, I wonder if there is a work-around that I could employ?

Or, if not, would it be wise of me to switch to another version of the OS.  If so, which version should I use?

Now that I've tasted Ubuntu Paradise, I really don't wish to go back to the Seven Levels of XP Misery!  HELP!

---

### Post by syn` on 2008-01-14
> **Colin The New Guy said:**
> Hello all!

I decided this weekend past to finally see what all the buzz was surrounding Ubuntu, so I've downloaded and installed a copy of 7.10 for my 64 system.  So far, I'm really liking what I've seen, particularly the level of community involvement.  You people are awesome.

In any case, I was hoping I could get some help with this issue.  I'm running a Radeon 9250  video card, and after some initial difficulty installing surrounding my display, I've been through the forums to see about a driver to make my video card work properly.  Currently I have to have visual effects off, and anything 3D makes my system slow to an absolute crawl, which is really sad because I'd love to be able to employ a few effects... and maybe a reasonable screen resolution.

I've done some homework;  I've followed a few suggestions from other threads without success, the final one I tried involved using a program called "Envy" which automated downloading of drivers and installing them from the ATI website.  I had hoped that my problem was solved, but in the end I received a message that there is no support for the Radeon 9250 on this version of the OS.

With that in mind, I wonder if there is a work-around that I could employ?

Or, if not, would it be wise of me to switch to another version of the OS.  If so, which version should I use?

Now that I've tasted Ubuntu Paradise, I really don't wish to go back to the Seven Levels of XP Misery!  HELP!


I can't really help, so don't get excited thinking this reply is going to be any of that. But if it makes you feel any better, I have the same problem. 

I haven't used Ubuntu but for a few days, but when I installed 7.4 a while back (I have the same card, btw) it never gave me an error with Envy about the Legacy driver not being supported. Weird stuff.

---

### Post by JoshuaRL on 2008-01-14
You might try the DRI open source drivers.  They're the ones I use for my Radeon Mobility 7500 that fglrx doesn't support.  It takes a little more work, and sometimes doesn't support every feature.  But it's better than running off of vesa all the time.  Could you post your xorg.conf?

---

### Post by Rocket2DMn on 2008-01-14
Just an FYI if it's immediately relevant - [https://help.ubuntu.com/community/Radeon_9200/9250_(RV280)_and_DVI](https://help.ubuntu.com/community/Radeon_9200/9250_(RV280)_and_DVI)
You can probably use the Feisty stuff for Gutsy.

---

### Post by Colin The New Guy on 2008-01-15
> **syn` said:**
> I haven't used Ubuntu but for a few days, but when I installed 7.4 a while back (I have the same card, btw) it never gave me an error with Envy about the Legacy driver not being supported. Weird stuff.

So perhaps it will be worth going back and seeing if I can get it to work in that, as a last-ditch effort.  Thanks!

> **JoshuaRL said:**
> You might try the DRI open source drivers.  They're the ones I use for my Radeon Mobility 7500 that fglrx doesn't support.  It takes a little more work, and sometimes doesn't support every feature.  But it's better than running off of vesa all the time.  Could you post your xorg.conf?

Thanks for your help!  Where would I find these DRI open source drivers?

I'll see about posting my xorg.conf when I'm at home this evening.  You just want the contents of the file?

> **Rocket2DMn said:**
> Just an FYI if it's immediately relevant - [https://help.ubuntu.com/community/Radeon_9200/9250_(RV280)_and_DVI](https://help.ubuntu.com/community/Radeon_9200/9250_(RV280)_and_DVI)
You can probably use the Feisty stuff for Gutsy.

This seems fairly step-by-step, I should be able to do it.  I'll post again this evening and say how it went.  Thank you!

---

### Post by JoshuaRL on 2008-01-15
Yeah post the output of:

```

sudo gedit /etc/X11/xorg.conf

```

If you want to install and use the DRI drivers I could help with that, but it will take a little bit.  So we'll go there if you need to.

---

### Post by Colin The New Guy on 2008-01-15
As requested.

> 
# xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"stylus"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"eraser"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"cursor"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"ATI Technologies Inc RV280 [Radeon 9200 PRO]"
	Driver		"ati"
	BusID		"PCI:1:1:0"
EndSection

Section "Monitor"
	Identifier	"AL1916W"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies Inc RV280 [Radeon 9200 PRO]"
	Monitor		"AL1916W"
	DefaultDepth	24
	SubSection "Display"
		Modes		"1440x1440" "1440x900" "1400x1050" "1280x1280" "1280x1024" "1280x960" "1152x921" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"

# Uncomment if you have a wacom tablet
#	InputDevice     "stylus"	"SendCoreEvents"
#	InputDevice     "cursor"	"SendCoreEvents"
#	InputDevice     "eraser"	"SendCoreEvents"
EndSection

---

### Post by Colin The New Guy on 2008-01-16
> **Rocket2DMn said:**
> Just an FYI if it's immediately relevant - [https://help.ubuntu.com/community/Radeon_9200/9250_(RV280)_and_DVI](https://help.ubuntu.com/community/Radeon_9200/9250_(RV280)_and_DVI)
You can probably use the Feisty stuff for Gutsy.

Sorry, in the end this didn't work.  It started being unable to find files and things, so maybe there are differences between FF and GG.  Though I suppose it's possible that I used it wrong through simple inexperience, I am not adept at reading the code that konsole is outputting.  Thanks anyway!

---

### Post by macogw on 2008-01-16
```
Section "Device"
Identifier "ATI Technologies Inc RV280 [Radeon 9200 PRO]"
Driver "ati"
BusID "PCI:1:1:0"
EndSection
```

That says you're already using the open source drivers.  See how driver says "ati"?  Those should work.  The closed-source fglrx drivers (what Envy installs) will slow it to a crawl (probably 1fps, and menus can't even open or anything)...I've seen it on OpenSuSE *shudder*.  If you run ```
glxinfo | grep direct
```, what do you get?  If it says no, can you paste the full output of ```
glxinfo
```?

---

### Post by Colin The New Guy on 2008-01-16
Output of ```
glxinfo | grep direct
``` is "Yes"

So maybe it's not the driver?

I'm still having to run the system with visual effects off, in order to avoid slowness.

In the past two nights, I've also started having the system start outputting uninterpretable signals to my monitor (at least, that's what my monitor says) seemingly at random.

---

### Post by Colin The New Guy on 2008-01-16
It appears I've started having the same problem in Windows, so perhaps this is a hardware issue after all.

I'm going to close this thread up.  I really appreciate your help, though!  Thanks!

---

