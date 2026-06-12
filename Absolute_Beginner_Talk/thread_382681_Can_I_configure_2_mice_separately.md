---
title: "Can I configure 2 mice separately?"
date: 2007-03-12
forum: Absolute Beginner Talk
---

### Post by cprsize on 2007-03-12
I'm not sure if this should be a Gnome question or an X question, but I figured I'd start here.

I work in a shop where we Pair Program 95% of the time.  I'm running Edgy w/ 2 monitors, 2 keyboards, 2 mice.

I'd like to be able to run my mouse left-handed, but have my Pair run right-handed.  I see lots of discussion of KVM situations and people trying to have 2 pointers.  I just want to be able to run two mice with two button configurations.  Google hasn't been too useful yet, so I figured I'd ask some people.

Suggestions?  Pointers?

--dwf

---

### Post by Bachstelze on 2007-03-12
Just add two InputDevice sections in your xorg.conf. If you have two mice plugged in, you should have /dev/input/mouse0 and /dev/input/mouse1. To whow which is which, do gor example

```
sudo cat /dev/input/mouse0
```

and mouve your mouse. If you see some random junk appearing on your terminal, that's the right one and you can do Ctrl+C to get back to your prompt.

Hope that helps :)

---

### Post by cprsize on 2007-03-12
OK.  I sort of tried that and I'm still not quite there.

Before my xorg.conf looked like this:

```
Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ExplorerPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection
```

This worked fine and both mice control the single pointer.

Now it looks like this:
```
Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mouse0"
	Option		"Protocol"		"ExplorerPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Identifier	"Other Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mouse1"
	Option		"Protocol"		"ExplorerPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

```


X/gdm is running fine, and Preferences/Mouse controls mouse0. But how do  I configure "Other Mouse" to be right-handed?

thx,
--dwf

---

