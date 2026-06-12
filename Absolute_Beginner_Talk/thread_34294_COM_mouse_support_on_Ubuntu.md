---
title: "COM mouse support on Ubuntu?"
date: 2005-05-14
forum: Absolute Beginner Talk
---

### Post by dunkmaster on 2005-05-14
ok, i have installed ubuntu 5.04. i have serial mouse on this machine and i want to know if ubuntu supports COM mice. atm it says that i have PS/2 mouse. mouse isnt functioning when i boot up to Gnome

---

### Post by nad on 2005-05-14
Serial mice are not autoconfigured in ubuntus' xorgs implemention.

You will need to edit your /etc/X11/xorg.conf file (as the superuser).

Find this section:

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/ttyS0"
	Option		"Protocol"		"Microsoft"
	Option		"Emulate3Buttons"	"true"
	Option		"ZAxisMapping"		"4 5"
EndSection

and change the Option "Device" and Option "Protocol" lines as above (that is a zero in the /dev/ttyS0 line). This should correctly address a two button, no scroll wheel serial mouse on com port 1.

If this doesn't work, please read the mouse man page for a description of other supported protocols that you may use.

---

### Post by dunkmaster on 2005-05-14
thank you very much. it helped, but it wasnt /dev/ttyS0 , but /dev/ttyS1  :) 

all working and im happy. :P

---

### Post by nad on 2005-05-14
Glad I could help and glad you could take it from there.

One never knows, do one?

---

### Post by Mujaheiden on 2006-03-13
any tips as to how to activate the mousehweel of my serial mouse? the mouse man is silent on this topic.

---

### Post by mlind on 2006-03-13
[QUOTE=Mujaheiden]any tips as to how to activate the mousehweel of my serial mouse? the mouse man is silent on this topic.[/QUOTE]

You've got Logitech's MouseMan? I have MouseMan optical and here's how my
xorg.conf entry looks like

```

 Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ExplorerPS/2"
        Option          "Emulate3Buttons"       "true"
        Option          "ZAxisMapping"          "4 5"

```

you can also try to reconfigure your mouse by doing
```

sudo dpkg-reconfigure xserver-xorg

```

---

### Post by Mujaheiden on 2006-03-13
The dpkg reconfigure did nothing except de-microsofting the protocol, which was annoying.
No, its not a logitech. Its my housemates computer - which has a "Chic, scroll serial mouse" attached. Other suggestions?

---

