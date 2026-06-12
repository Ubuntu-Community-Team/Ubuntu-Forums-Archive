---
title: "No right click, Samsung QX"
date: 2012-02-15
forum: Any Other OS
---

### Post by nine9nine on 2012-02-15
Hi everyone.  I have OpenSUSE 12.1 Gnome installed on my Samsung QX laptop.  Everything seems to work, except right-clicking.  The touchpad has the buttons built into it, and with Windows I can use those, or 2-finger click to right-click.  With OpenSUSE, I can 2-finger scroll, so I know it has multitouch support, but I don't know how to get it to right-click, 2-fingered or the built in right-click button.  A wireless mouse can right-click, so I have to use that, but it would be nice to be able to use the touchpad.  Does anyone know any way, GUI or a configuration file, to solve this problem?

---

### Post by winh8r on 2012-02-15
This thread might help you:

[http://ubuntuforums.org/showthread.php?p=11350400#post11350400]("http://ubuntuforums.org/showthread.php?p=11350400#post11350400")

in particular the post by Roadmaster at #18

hope this helps you.

---

### Post by nine9nine on 2012-02-15
Hmm... I don't think that will work for me.  OpenSUSE is recognizing the touchpad, but doesn't right-click, and I prefer actually clicking the touchpad, since it has the buttons built in, and not just tapping, because I always end up clicking by accident.  Is there any config file I can edit to get it to right-click when I click with 2-fingers?

---

### Post by winh8r on 2012-02-16
try entering this in a terminal:


```
xinput list
```

this will identify all input devices by id

then enter

```
xinput --list-props <the id number of your touchpad from the above command>
```


this will display the current parameters


the command:

```
sudo tpconfig 
```

should allow you to set/adjust the configuration. I haven't had to use this but am currently trying it out on an old laptop I have lying around.

hope this helps.

---

### Post by nine9nine on 2012-02-16
OK, when I use ```
xinput --list-props 12
``` I get ```
Device Enabled (132):	1
	Coordinate Transformation Matrix (134):	1.000000, 0.000000, 0.000000, 0.000000, 1.000000, 0.000000, 0.000000, 0.000000, 1.000000
	Device Accel Profile (250):	1
	Device Accel Constant Deceleration (251):	2.500000
	Device Accel Adaptive Deceleration (252):	1.000000
	Device Accel Velocity Scaling (253):	12.500000
	Synaptics Edges (254):	123, 2974, 96, 1697
	Synaptics Finger (255):	25, 30, 256
	Synaptics Tap Time (256):	180
	Synaptics Tap Move (257):	157
	Synaptics Tap Durations (258):	180, 180, 100
	Synaptics Tap FastTap (259):	0
	Synaptics Middle Button Timeout (260):	75
	Synaptics Two-Finger Pressure (261):	282
	Synaptics Two-Finger Width (262):	7
	Synaptics Scrolling Distance (263):	71, 0
	Synaptics Edge Scrolling (264):	0, 0, 0
	Synaptics Two-Finger Scrolling (265):	1, 1
	Synaptics Move Speed (266):	1.000000, 1.750000, 0.055897, 40.000000
	Synaptics Edge Motion Pressure (267):	30, 160
	Synaptics Edge Motion Speed (268):	1, 286
	Synaptics Edge Motion Always (269):	0
	Synaptics Off (270):	0
	Synaptics Locked Drags (271):	0
	Synaptics Locked Drags Timeout (272):	5000
	Synaptics Tap Action (273):	0, 0, 0, 0, 0, 0, 0
	Synaptics Click Action (274):	1, 1, 1
	Synaptics Circular Scrolling (275):	0
	Synaptics Circular Scrolling Distance (276):	0.100000
	Synaptics Circular Scrolling Trigger (277):	0
	Synaptics Circular Pad (278):	0
	Synaptics Palm Detection (279):	0
	Synaptics Palm Dimensions (280):	10, 200
	Synaptics Coasting Speed (281):	20.000000, 50.000000
	Synaptics Pressure Motion (282):	30, 160
	Synaptics Pressure Motion Factor (283):	1.000000, 1.000000
	Synaptics Grab Event Device (284):	1
	Synaptics Gestures (285):	1
	Synaptics Capabilities (286):	1, 0, 1, 1, 1, 1, 1
	Synaptics Pad Resolution (287):	1, 1
	Synaptics Area (288):	0, 0, 0, 0
	Synaptics Noise Cancellation (289):	17, 17
	Synaptics Touch Button Area (290):	20
	Synapyics Touch Button Sticky (291):	64
	Synaptics LED (292):	0
	Synaptics LED Status (293):	0
	Synaptics LED Dobule Tap (294):	1
	Device Product ID (295):	2, 14
	Device Node (296):	"/dev/input/event1"

```

However, when I use ```
sudo tpconfig
``` it says that the command isn't found.  Is there another way I can adjust the settings?

---

### Post by winh8r on 2012-02-16
If it is not found then 


```
sudo apt-get install tpconfig
```


then run

```
tpconfig --info
```

hope this helps

---

### Post by winh8r on 2012-02-16
Found this, which is probably what you need:


[http://ubuntuforums.org/showthread.php?t=1737086&highlight=samsung+touchpad]("http://ubuntuforums.org/showthread.php?t=1737086&highlight=samsung+touchpad")

---

### Post by nine9nine on 2012-02-17
Neither of those worked for me.  It's probably because I'm on OpenSUSE, and those are for Ubuntu.  I can't even find any package for tpconfig.  Do you know anything else?

---

### Post by nine9nine on 2012-02-18
New problem.  I installed a vanilla kernel, and now I have right clicking.  However, I can no longer scroll, or disable tap-to-click, and when I try to use ```
synclient TapButton1=0
``` I get ```
Couldn't find synaptics properties. No synaptics driver loaded?
```  Any ideas to fix this issue, or would it be easier to get right click on the other kernel?

---

