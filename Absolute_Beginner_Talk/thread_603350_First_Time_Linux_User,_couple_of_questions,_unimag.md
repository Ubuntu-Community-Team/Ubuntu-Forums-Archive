---
title: "First Time Linux User, couple of questions, unimaginative forum title."
date: 2007-11-05
forum: Absolute Beginner Talk
---

### Post by Cravethought on 2007-11-05
Well, it's my first time using Linux, and while Ubuntu looks pretty, I've been trying to get my 7 button mouse to go "Back" and "Forward" like it used to for about an hour now. 7 buttons includes my mouse wheel + and -, as well as middle click. I want my mouse buttons 3 and 4 (on the sides) to function as the "back" and forward" buttons in Firefox and explorer as opposed to "Paste" and "Right Click" (which they are now).

Before you link me here, I've tried already, and this is what I've come up with:

My /etc/X11/xorg.conf for my mouse looks like this:
```
Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"        "/dev/input/mice"
        Option          "Protocol"      "ImPS/2"
        Option          "Emulate4Buttons"       "false"
        Option          "Buttons"       "7"
        Option          "ZAxisMapping"  "4 5"
        Option          "ButtonMapping" "1 2 3 6 7"
EndSection

```

When I load imwheel -c, it registers that my buttons on the sides are buttons 6 and 7 (or did, two seconds ago. I just tried it and nothing came up.)

This is my entry for firefox in /etc/X11/imwheel/imwheelrc

```
"^Firefox-bin$"
None,Left,Alt_L|Left
None,Right,Alt_L|Right

```

Also, as I've been messing around in the console, I was wondering: is there was any way to check to see if my modifications have worked without restarting my computer? I edit the text file and I don't want to have to go through the enormous process of restarting just to see if I win or not.

It's been a bit frustrating. But I want to get this working.

---

### Post by bubbalouie on 2007-11-05
CTRL + ALT + Backspace will reboot X, you can test changes that way

I have 7 buttons working, and no IMWheel is needed, example config is below (Emulate3buttons=false, and a different protocol seem to be only differences):

```
Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"	"/dev/input/mice"
	Option		"Protocol"	"ExplorerPS/2"
	Option		"Emulate3Buttons"	"false"
	Option		"Buttons" "7"
	Option		"ButtonMapping" "1 2 3 6 7"
	Option		"ZAxisMapping" "4 5"
EndSection
```

---

### Post by Cravethought on 2007-11-05
Forsooth, it works! Hell yes.

Thank you.

---

### Post by bubbalouie on 2007-11-05
Glad to help :)

---

