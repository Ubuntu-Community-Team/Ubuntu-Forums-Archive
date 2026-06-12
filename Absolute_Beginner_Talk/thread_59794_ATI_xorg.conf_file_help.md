---
title: "ATI xorg.conf file help"
date: 2005-08-25
forum: Absolute Beginner Talk
---

### Post by jasonpeinko on 2005-08-25
i need help setting up the parramiters for my mouse and keyboard.
	
this is the mouse ```

Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"Emulate3Buttons"	"true"
	Option		"ZAxisMapping"		"4 5"

```
this is the keyboard```

	Identifier	"Generic Keyboard"
	Driver		"keyboard"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc104"
	Option		"XkbLayout"	"us"

```
i dont know what to put for the Options. i have a zboard gaming keyboard and i know zboard does not have linux drivers yet buy the keyboard works. It has a num pad and all the standard buttons.
for my mouse i have a Logitech mx 1000 cordless mouse with 3 thumb buttons up and down and side to side scroll wheel and up and down scroll buttons.

---

### Post by jyank on 2005-08-25
Do the mouse buttons not work at all?

I have an MX 518 which has 8 buttons, and my config looks like so:

```
Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"ExplorerPS/2"		"ImPS/2"
	Option		"Resolution"		"800"
	Option		"ZAxisMapping"		"4 5"
	Option		"Buttons"		"10"
EndSection

```

Restart x after chaning

Not sure about the zboard though, don't have one sorry :(

---

### Post by jasonpeinko on 2005-08-25
[QUOTE=jyank]Do the mouse buttons not work at all?

I have an MX 518 which has 8 buttons, and my config looks like so:

```
Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"ExplorerPS/2"		"ImPS/2"
	Option		"Resolution"		"800"
	Option		"ZAxisMapping"		"4 5"
	Option		"Buttons"		"10"
EndSection

```

Restart x after chaning

Not sure about the zboard though, don't have one sorry :([/QUOTE]
 if i leave the file as is in the mouse section will it work as it does right now?

---

### Post by jyank on 2005-08-25
It should but all of the buttons might now work properly

---

