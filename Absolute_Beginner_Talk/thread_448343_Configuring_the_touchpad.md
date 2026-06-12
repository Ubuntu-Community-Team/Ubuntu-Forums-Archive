---
title: "Configuring the touchpad"
date: 2007-05-19
forum: Absolute Beginner Talk
---

### Post by emlarsen on 2007-05-19
I downloaded the GSynaptics touchpad software, but I don't think i have a synaptics touchpad. I have a Dell inspiron 6000 laptop, and need to configure the touchpad, but when I try I get an error message saying "You have to set SHMConfig 'true' in xorg.conf or XF86 config to use GSynaptics. 

To be frankly honest, I dont know what that means, or how to solve this problem. Could someone please help? :-)

---

### Post by Gen2ly on 2007-05-19
Hello there.  Configuring your xorg.conf is simple.  Need to just:

```
sudo gedit /etc/X11/xorg.conf
```

Find the part on Synaptic and add that line.  Here's a look at mine:
```

Section "InputDevice"
    Identifier      "Synaptics Touchpad"
    Driver          "synaptics"
    Option          "SendCoreEvents"        "true"
    Option          "Device"                "/dev/psaux"
    Option          "Protocol"              "auto-dev"
    Option          "HorizScrollDelta"      "0"
    Option          "SHMConfig"             "true"
```

---

### Post by mahy on 2007-05-19
Sure. Open the xorg.conf file:

```
sudo gedit /etc/X11/xorg.conf
```

Then find the stanza about your synaptics touchpad (it should be easy!) and put there a line reading

```
Option		"SHMConfig"	"on"
```

This is the entire stanza:

```
Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"	"/dev/psaux"
	Option		"Protocol"	"auto-dev"
	Option		"VertScrollDelta"	"0"
	Option		"HorizScrollDelta"	"0"
	Option		"SHMConfig"	"on"
EndSection
```

HTH!

---

### Post by emlarsen on 2007-05-19
I do that but the xorg.conf file is blank? why?

---

### Post by emlarsen on 2007-05-19
...?

---

### Post by mahy on 2007-05-19
Impossible. Very likely you made a typo or entered a letter in a wrong case (i.e. "x11" instead of "X11").

---

### Post by emlarsen on 2007-05-19
you're right. I did that, I saved it, but the touchpad gsynaptics still doesn't work :-\

---

### Post by mahy on 2007-05-19
> **emlarsen said:**
> you're right. I did that, I saved it, but the touchpad gsynaptics still doesn't work :-\

You have to reboot the X server (Ctrl+Alt+Backspace) or the entire computer for the changes to take effect! :lolflag:

---

### Post by emlarsen on 2007-05-19
Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizScrollDelta"	"0"
	Option          "SHMConfig"             "on"
EndSection

That's exactly what it says in my xconfig.conf file.

---

### Post by emlarsen on 2007-05-19
lol woops. I got it now. 

<----N00b.


Thanks A Lot!

---

### Post by mahy on 2007-05-19
You're welcome.  :guitar:

---

