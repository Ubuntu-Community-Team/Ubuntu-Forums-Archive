---
title: "PLEASE HELP ME my mouse goes to the right click menu by itself"
date: 2006-10-02
forum: Absolute Beginner Talk
---

### Post by sociallyteamed on 2006-10-02
My mouse, i have a USB for my laptop, wherever i point it at, will go to the right click menu, like i cant hant even use my computer cause the menu will appear out of its own accord .PLEASE HELP ME
the problem first appeared when i used the touchpad in the IBM t30
thank you

---

### Post by PPAAUULL on 2006-10-02
Is it just on the touchpad or on a external mouse aswell?

---

### Post by sociallyteamed on 2006-10-02
now its on both it used to be just mouse but now its both, the left click button on the touchpad just acts like a right click now

---

### Post by PPAAUULL on 2006-10-02
Have you tryed going into the mouse settings?

---

### Post by Buffalo Soldier on 2006-10-02
At to top panel, go to System -> Preferences -> Mouse

---

### Post by PPAAUULL on 2006-10-02
> **Buffalo Soldier said:**
> At to top panel, go to System -> Preferences -> Mouse

Exacly what I was thinking!!!

---

### Post by sociallyteamed on 2006-10-02
YOU must think im retarded, i already tried that

---

### Post by PPAAUULL on 2006-10-02
No we don't we just go from easy to advanced.

You are sure you have the correct driver?

---

### Post by Buffalo Soldier on 2006-10-03
> **sociallyteamed said:**
> YOU must think im retarded, i already tried that
No, we don't :)

What kind of mouse are you using actually? How about posting your **xorg.conf** file here? Here's the mouse part of my xorg.conf f. Mind that I'm using a trackball on the left hand. 

```
Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ExplorerPS/2"
	Option		"Emulate3Buttons"	"true"
	Option		"Buttons"		"9"
	Option		"EmulateWheel"		"1"
	Option		"EmulateWheelButton"	"9"
	Option		"YAxisMapping"		"4 5" 
	Option		"XAxisMapping"		"6 7" 
EndSection
```

---

