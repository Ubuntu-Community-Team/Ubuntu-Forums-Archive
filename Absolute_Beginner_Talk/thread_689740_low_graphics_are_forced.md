---
title: "low graphics are forced"
date: 2008-02-06
forum: Absolute Beginner Talk
---

### Post by ins0mn1ax on 2008-02-06
I have just tried to set my Logitech MX518 mouse up with a guide I found on here, and changed the mouse driver to evdev:

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"evdev"
	Option		"CorePointer"
	Option		"Device"	"/dev/input/mice"
	Option		"Protocol"	"ImPS/2"
	Option		"ZAxisMapping"	"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

However, I (foolishly) did not make a backup of the working xorg.conf, and didn't note down what the Driver was set to. As a result, whenever I boot it does not detect my x1950 graphics card and is forced into low graphics mode.

I have tried re-running envy to reinstall the driver for my card, and it hasn't helped. What is the default setting for the mouse driver? It is the only thing I have changed, so I'm hoping that changing it back will restore my standard graphics settings!

---

### Post by pmshirey on 2008-02-06
The easiest thing here would be to make sure that all the graphic drivers are installed. Also, there may be an even more serious problem, if you are using a wireless mouse, it may only be for windows, though I am using a Microsoft brand mouse on Linux. What are the specs of your mouse?

---

### Post by pmshirey on 2008-02-06
Also, you may not have the driver installed on your graphics card. Do some research on Linux READ MEs.

---

