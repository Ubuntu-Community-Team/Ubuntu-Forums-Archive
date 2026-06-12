---
title: "Compaq Mouse Problems"
date: 2006-09-04
forum: Absolute Beginner Talk
---

### Post by alienexplorers on 2006-09-04
I have a Compaq mouse that came with my system and It has worked fine since installing ubuntu 6.06 LTS. About a week ago several updates were done on my machine and now my mouse is working like a piece of junk. The buttons are not working properly and the optical tracking is off. The mouse cursor seems to move where ever it wants, the buttons are acting like I have double clicked when I only single clicked it. Other times I double click and it acts like it was single clicked. Tried a old M$ mouse and it has the same problems. I am posting my Xorg.conf Mouse section here:

Section "InputDevice"
Identifier "Configured Mouse"
Driver "mouse"
Option "CorePointer"
Option "Device" "/dev/input/mice"
Option "Protocol" "ExplorerPS/2"
Option "Emulate3Buttons" "true"
Option "ZAxisMapping" "4 5"
EndSection

Everything looks OK to me, but I may be wrong. The mouse again is a Compaq (No model number). It has 2 buttons and a scroll wheel/button. It also has optical tracking.

Thanks in advance,

Donald

---

### Post by alienexplorers on 2006-09-04
Help Please.....Bounce

---

### Post by greyghost60 on 2006-09-04
My M$ mouse is working fine 
Here is my bit of the file 

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ExplorerPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

The only difference seems to be the swap of the last 2 lines 

I don't know if the final section 

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus" "SendCoreEvents"
	InputDevice     "cursor" "SendCoreEvents"
	InputDevice     "eraser" "SendCoreEvents"
EndSection
 has anyting to do with it.

Greyghost

---

