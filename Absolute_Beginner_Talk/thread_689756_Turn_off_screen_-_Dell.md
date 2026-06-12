---
title: "Turn off screen - Dell"
date: 2008-02-06
forum: Absolute Beginner Talk
---

### Post by cartisdm on 2008-02-06
I have a Dell e1505 using a x1400 graphics card how can I get my screen to turn off after a while?  It goes blank but I'd prefer if it turned off after like 20 minutes or so

---

### Post by jordanmthomas on 2008-02-06
Add this to the Monitor section in your xorg.conf
```
Option   "DPMS"
``` and the monitor should be able to turn itself off.

Then, to get it to automatically shut off after a certain time, put this in the ServerLayout section
```
Option "OffTime" "20"
``` where 20 is the number of minutes you'd like to wait.


[COLOR="Red"]//slightly offtopic[/COLOR]
Also, to turn the monitor off arbitrarily you can run this:
```
xset -display :0 dpms force off
```
(I used xbindkeys to bind this to my laptop's stop button since I don't use stop anyway.  Then, any time I leave I just give the stop button a tap and the screen turns off.)

---

### Post by cartisdm on 2008-02-06
It didn't work.  Here's what I did, I already had the first part in the monitor sections
```
Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
EndSection

Section "Monitor"
	Identifier	"aticonfig-Monitor[0]"
	Option		"VendorName"	"ATI Proprietary Driver"
	Option		"ModelName"	"Generic Autodetecting Monitor"
	Option		"DPMS"	"true"
EndSection
```

And in the server layout
```
Section "ServerLayout"
	Identifier	"Default Layout"
  screen 0 "aticonfig-Screen[0]" 0 0
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
	Inputdevice	"stylus"	"SendCoreEvents"
	Inputdevice	"cursor"	"SendCoreEvents"
	Inputdevice	"eraser"	"SendCoreEvents"
	Inputdevice	"Synaptics Touchpad"
	Option "OffTime" "5"
EndSection
```

---

### Post by jordanmthomas on 2008-02-06
First:  a dumb question, have you restarted X since editing xorg.conf?

Second:  will the screen turn off if you run
```
xset -display :0 dpms force off
```

Third:  it could be that gnome is taking over the shutdown of the screen.  Look for a power management preferences somewhere in your menus (don't use Gnome, so I can't tell you exactly where).  There may be an option for it in there.

Fourth:  It may be an option in your screensaver options.  I don't use a screensaver either (and I'd certainly not use gnome-screensaver, which is what Ubuntu ships with) so I'm not sure there either.  However, I vaguely remember it being there in xscreensaver, so perhaps it's there in gnome-screensaver as well.

---

### Post by LarryJ2 on 2008-02-06
try   System Settings ->Monitor & Display   Power Saving  then  click Admin mode  and give your password.     There you can  then set the time before the monitor shuts off.

This works on my dell  e1505 laptop with  Gutsy  7.10 Desktop install   My display also shuts off when I close the lid.   I don't know what causes that.   Just came with the installation.

---

### Post by jordanmthomas on 2008-02-06
> **LarryJ2 said:**
> try   System Settings ->Monitor & Display   Power saving  then  click Admin mode  and give your password.     There you can  then set the time before the monitor shuts off.


Well, looky there!  Why must I always do things the hard way?   :popcorn:

> My display also shuts off when I close the lid. I don't know what causes that.
Probably overcomplicating it again, but the file at /etc/acpi/lid.sh controls what happens on lid shuts/opens

---

### Post by cartisdm on 2008-02-06
> **jordanmthomas said:**
> First:  a dumb question, have you restarted X since editing xorg.conf?


Yeah so......I forgot to reboot and it works perfect now:D

Thanks!

---

