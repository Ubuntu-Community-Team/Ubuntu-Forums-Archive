---
title: "Need Synaptics touchpad walkthrough"
date: 2005-12-21
forum: Absolute Beginner Talk
---

### Post by hhh on 2005-12-21
My Gateway laptop had little working out of the box with 1.5, but I've struggled to get it working (I've fixed ethernet, wireless [the dreaded Brroadcom card/ndiswrapper nightmare], switch networks via network-manager, boot up time, upgraded Firefox to 1.5, sound from CD rom [disable external speaker], autoplay protected DVDs in Ogle, fixed crackly sound/choppy playback, but I'm stuck on the touchpad (not bad for a COMPLETE Linux n00b though, eh?).

I've read a lot of threads on this but whenever I try to follow a step by step I get to edit xorg.conf and reboot and then I'm screwed. It reboots without GUI and I have to dbpkg-reconfigure to get my desktop back. After a few different versions of this I now have the same touchpad tapping problems (I can barely post this, the cursor goes nuts) plus left clicking my desktop icons (windows partition, Computer, Home) does nothing, I can only open them via the context menu. Ideas?

```
I: Bus=0011 Vendor=0002 Product=0007 Version=0000
N: Name="SynPS/2 Synaptics TouchPad"
P: Phys=isa0060/serio1/input0
H: Handlers=mouse0 event1 ts0
B: EV=b
B: KEY=6420 0 70000 0 0 0 0 0 0 0 0
B: ABS=11000003

```

```
Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizScrollDelta"	"0"
EndSection
```

---

### Post by Sef on 2006-01-12
My laptop's cursor went crazy too.  Finally I just went into the boot menu and turned off the touchpad.  Works fine now.  Sometimes those touchpads just don't work right.  Have usb mouse and it works with no problem.

---

### Post by Viciou§ on 2006-01-12
I had some trouble with my touchpad though not the same as you.
In my case I didn't have the synaptics_drv.o on my system.
There's a guide somewhere in this forum describing how to install it.
Just download tar archive, unpack, make and make install and it worked for me.

---

