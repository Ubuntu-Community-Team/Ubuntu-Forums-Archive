---
title: "slowdown after update?"
date: 2007-04-23
forum: Absolute Beginner Talk
---

### Post by jtx472 on 2007-04-23
Ubuntu 7.04 has been working just fine since  I installed but I downloaded some updates this morning and it slowed down to a crawl.  It takes minutes for  my desktop to loadup and the same for every window I try to open???

---

### Post by tact on 2007-04-23
Had a similar occurance.  No idea what caused it.  After some time half a dozen windows all opened (the ones I had clicked on repeatedly when no response) and the system was back up to speed.   Rebooted just to be safe.  ;)

Has not repeated again today.  Monitoring.

---

### Post by jtx472 on 2007-04-23
Well I've rebooted several times and it's still doing the same thing.  If I can't find a fix I guess I'll just have to re-install cause I can't handle this.  Thanks for your reply.

---

### Post by tact on 2007-05-03
Wooohooo got my system back up to speed!

When the system was running slow - and I looked at system monitor or "top" on the commandline I could see no problem there...  nothing was maxing out the CPU.  So I wondered if some system internals were fighting and tying things up...and since they are not applications as such perhaps not seen in system monitor.

I went back through all the tweaking and tinkering I had done on any system internals.... to see if I had caused the slow down.  I had for example done the "dpkg-reconfigure xserver-xorg" thing to see if I could get more than one screen resolution (it worked and also got my touchpad working properly so that scrolling and right clicks are handled on the touchpad).

I found nothing interesting in my xorg.conf except the reconfigure had put reference to the wacom tablet device and I don't have one.  Always figured thats a harmless default but what the heck  -  lets comment it out and see if it makes a difference.  

It made a difference!   Speed back to normal.

I commented out these lines:
#Section "InputDevice"
#	Driver		"wacom"
#	Identifier	"stylus"
#	Option		"Device"	"/dev/input/wacom"
#	Option		"Type"		"stylus"
#	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
#EndSection

#Section "InputDevice"
#	Driver		"wacom"
#	Identifier	"eraser"
#	Option		"Device"	"/dev/input/wacom"
#	Option		"Type"		"eraser"
#	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
#EndSection

#Section "InputDevice"
#	Driver		"wacom"
#	Identifier	"cursor"
#	Option		"Device"	"/dev/input/wacom"
#	Option		"Type"		"cursor"
#	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
#EndSection


and at the bottom of the file these lines:
#	InputDevice     "stylus"	"SendCoreEvents"
#	InputDevice     "cursor"	"SendCoreEvents"
#	InputDevice     "eraser"	"SendCoreEvents"

---

