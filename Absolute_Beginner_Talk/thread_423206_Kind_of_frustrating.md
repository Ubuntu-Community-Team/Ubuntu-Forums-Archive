---
title: "Kind of frustrating"
date: 2007-04-25
forum: Absolute Beginner Talk
---

### Post by sirdeuce on 2007-04-25
I'm using the Kubuntu Live CD (amd64 version) right now on my ATI Radeon X700 card. All I had to do to make it work after the screen kept going black when I tried to boot was change the VGA using F4 and then booting into Kubuntu. Looking around, I got the feel and decided to install. Went without a glitch, but it will NOT boot. All I get is a black screen. No sound, no text, nothing. I can get the recovery text version going after I restart my PC, if that means anything, but I cannot launch the desktop. I'm back on the LiveCD right now, and everything is fine. So, how do I make the version on my harddrive work like this CD does? Most of the things I read on how to change the driver or whatever all somehow seem to involve getting into the menu, and since i can't get into any menus when everything locks up and the screen goes black, this doesn't seem to be a help. So, if I'm in the recovery mode without a GUI, how can I change the settings to make my harddrive version work like this CD?

---

### Post by Seisen on 2007-04-25
Type this in the terminal

 vim /etc/X11/xorg.conf

Press shift + i and it will say Insert, then scroll down to here using the arrow keys.

```
Section "Device"
	Identifier	"Generic Video Card"
	Driver		"via"
	BusID		"PCI:1:0:0"
```

Change the driver to vesa and then press do this

```
:wq
``` This will write the file and save it. Then it should boot up fine and after that you can try to get your ATI card working.

---

