---
title: "Mouse Problems"
date: 2006-08-22
forum: Absolute Beginner Talk
---

### Post by alienexplorers on 2006-08-22
Ever since the last autoupdate of my system my mouse is working kind of odd.  When I click the right mouse button the menu will flash on and off several times before it stays enabled so I can select the function I want.  Also, when I move the mouse over info boxes (close, open, ect...) it distorts the typed letters in the box.

I am running a compaq optical USB mouse and never had these problems before.  tried setting up xorg again with no luck.  I am sending the mouse section of the xorg file to see if anyone can find something wrong.

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"Emulate3Buttons"	"true"
	Option		"ZAxisMapping"		"4 5"
EndSection

Donald Saunders

---

### Post by alienexplorers on 2006-08-22
Bounce

---

### Post by bodhi.zazen on 2006-08-22
Not sure about you mouse.

Try changing
```
Option "Emulate3Buttons" "true"
```

To:
```
Option "Emulate3Buttons" "false"
```

and
```
Option "Protocol" "ImPS/2"
```

To:
```
"Protocol" "ExplorerPS/2"
```

---

