---
title: "Five button mouse not responding, 6.06"
date: 2006-09-02
forum: Absolute Beginner Talk
---

### Post by Taigrr on 2006-09-02
I have a five button mouse, I -THINK- made by GE, but it's not for certain.

Scrollwheel, left and right buttons like a normal mouse, and one botton to each furthest side of the mouse, left to right.

When I plug it in, Ubuntu doesn't recognize it. The cursor won't even move. But, the optical-light on the mouse lights up and reacts to movment as it should, and the mouse has worked in Windows many many times. Any idea how to make it work?

---

### Post by croak77 on 2006-09-02
What does the mouse section look like in your /etc/X11/xorg.conf?

You might need something like this;

```
Identifier   "Mouse1"
  Driver       "mouse"
  Option       "Buttons" "5"
  Option       "Device" "/dev/input/mice"
  Option       "Protocol" "ExplorerPS/2"
  Option       "Vendor" "Sysp"
  Option       "ZAxisMapping" "4 5"

```

---

### Post by Anduu on 2006-09-03
My mouse section looks like this:

```
Section "InputDevice"
	Identifier "Configured Mouse"
	Driver "mouse"
	Option "CorePointer"
	Option "Device" "/dev/input/mice"
	Option "Buttons" "7"
	Option "Protocol" "ExplorerPS/2"
	Option "ButtonMapping" "1 2 3 7 6"
	Option "ZAxisMapping" "4 5"
	Option "Resolution" "800"
#	Option "Emulate3Buttons" "true"
EndSection
```

I was told to specify as 7 buttons for proper functionality as mousewheelup/down are considered "buttons" as well...Kind of counterintuitive I know but it works like a charm.

---

### Post by ron999 on 2006-09-03
Hi Taigrr

I'm using a 5 button mouse too. When I installed Ubuntu I was told to alter the mouse settings in the file /etc/X11/xorg.conf

This is the relevant section of the file:-

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ExplorerPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"false"
	Option		"Buttons"		"7"
	Option		"ButtonMapping"		"1 2 3 6 7"
EndSection


I got the info from here
[http://www.cs.cornell.edu/~djm/ubuntu/#update-sources](http://www.cs.cornell.edu/~djm/ubuntu/#update-sources)

The settings are very similar to Anduu above.

---

### Post by Burke on 2006-09-03
Excellent, that actually works for me!  I've always wanted to get my MX518 mouse working better, but I've never bothered asking. Thanks very much guys!

---

### Post by Burke on 2006-09-03
[COLOR="LightBlue"][SIZE="1"]Sorry, double post.[/SIZE][/COLOR]

---

### Post by Anduu on 2006-09-03
> **Burke said:**
> Excellent, that actually works for me!  I've always wanted to get my MX518 mouse working better, but I've never bothered asking. Thanks very much guys!

WooT !

---

