---
title: "Emulate3Buttons for other button than button2?"
date: 2008-03-08
forum: Absolute Beginner Talk
---

### Post by willywilly on 2008-03-08
I own a classic mouse with two buttons and a scrollwheel (that can be clicked as well).

I'm trying to set up that when I click Left+Right on this mouse, the Compiz Scale plugin is used. Right now this only triggers Button2, the same button as clicking on the scrollwheel (e.g. for opening new tabs in firefox). Here is my xorg.conf for now:

```
Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"	"/dev/input/mice"
	Option		"Protocol"	"ImPS/2"
	Option		"ButtonMapping" "1 2 3"
	Option		"ZAxisMapping"	"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection
```

How do I make it now that clicking the left+right does something other than click Button2?




My try was this:

```
Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"	"/dev/input/mice"
	Option		"Protocol"	"ImPS/2"
	Option		**"ButtonMapping" "1 6 3"**
	Option		"ZAxisMapping"	"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection
```

But now obviously Left+Right still does the old thing, but clicking the mousewheel is like pushing a backbutton. I dont know how to remap those commands now, otherwise I would be set.

---

### Post by pbpersson on 2008-03-08
I happen to think that if you have "emulate 3 button" set to true, that tells it to click button 2 when you hit both 1 and 3

I would set that to false

Also on mine I had to set the ImPS/2 to ExplorerPS/2

Don't ask me why, I read somewhere it was the thing to do  :confused:

---

