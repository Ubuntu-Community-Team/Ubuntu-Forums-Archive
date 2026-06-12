---
title: "Logitech MX3200 keyboard/mouse"
date: 2008-02-21
forum: Absolute Beginner Talk
---

### Post by poordamnedfool on 2008-02-21
Ubuntu recgonizes the mouse but it wont recognize the keyboard.  any ideas?

---

### Post by Presto123 on 2008-02-23
Go into your System/Preferences/Keyboard and select the "Layouts" tab. Try to test what is listed there.

---

### Post by rayzoredge on 2008-03-28
Just because I don't want to start up a new redundant topic...

I own this keyboard and mouse set and just got it to work the other day.

Edit your **xorg.conf** to reflect these changes under the mouse and keyboard sections:

```
Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"	"/dev/input/mice"
	Option		"Protocol"	"auto"
	Option		"Buttons"	"7"
	Option		"ZAxisMapping"	"4 5"
	Option		"ButtonMapping"	"1 2 3 6 7 4 5 6"
EndSection
```

Also, if you have access to a Windows machine or boot, I followed some advice and secured the encrypted signal by using SetPoint. Run SetPoint, go to your Keyboard wireless settings, and start the Secure Connection wizard.

This will allow you to use the mouse and keyboard in conjunction. Most special keys will have no function... I just tested the multimedia keys on the keyboard and the forward and back buttons on the mouse and they are just fine.

One thing to note, however: I've noticed that on the logon screen, if you move the mouse at all when prompted to type in your username and password, the mouse will move a quarter of an inch and then freeze, remaining unresponsive. (The keyboard will still work.) If, during this session, you unplug and re-insert the USB receiver, the mouse will work but with 1-second unresponsive times between 3-second functional intervals... and the keyboard won't work.

So in short, DON'T MOVE THE MOUSE ON LOGON. :-p

If anyone would like to elaborate on how to get the special function keys to work, feel free.

---

### Post by rayzoredge on 2008-03-29
I actually would like to add that the above method doesn't work 100% of the time... as of right now with an unchanged xorg.conf, for some reason I'm exhibiting the same problems as before: one working input device, the other being unresponsive.

Case is still open... :mad:

---

