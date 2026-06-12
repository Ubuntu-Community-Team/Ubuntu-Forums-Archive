---
title: "Newbie with two questions about Mouse Sensitivity and Trackpad Tapping"
date: 2006-08-25
forum: Absolute Beginner Talk
---

### Post by solipsism on 2006-08-25
Issue 1:
[INDENT]My mouse movement is very "loose" despite my adjustments with the mouse controls under System => Mouse in the Gnome desktop of Ubuntu 6. I've used WinXP on this same machine without issues.[/INDENT]

Issue 2:
[INDENT]I need a solution to turn off Trackpad Tapping. I've found some solution while Googling that had me apend various Option lines to the XORG.CONF file in /etc/X11, but that didn't resolve the issue (yes, I restarted). I've appended part of the file's default below... [INDENT][FONT="Century Gothic"]Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ExplorerPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection[/FONT][/INDENT]
I've also replaced the text above with the Synaptic driver info that I found in other posts but that didn't work.[/INDENT]


I am using Ubuntu 6.06 Desktop on a Compaq Preasrio 1201z notebook w/ 30GB HDD, 320MB RAM. I am open to command line solutions but I may have additonal questions as I haven't touched Linux for about 6 years now.

Thank you in advance for any assistance you can offer.

---

### Post by solipsism on 2006-08-25
bump

This trackpad tapping is such a pain int he ***. Please don't make me go back to Windows.

---

### Post by solipsism on 2006-08-26
bump

---

### Post by solipsism on 2006-08-27
I replaced part of the [COLOR="Blue"]/etc/X11/xorg.conf[/COLOR] file:
[SIZE="2"][COLOR="Blue"][INDENT]Section "InputDevice"
Identifier "Configured Mouse"
Driver "mouse"
Option "CorePointer"
Option "Device" "/dev/input/mice"
Option "Protocol" "ExplorerPS/2"
Option "ZAxisMapping" "4 5"
Option "Emulate3Buttons" "true"
EndSection[/INDENT][/COLOR][/SIZE]

With:
[SIZE="2"][COLOR="Blue"][INDENT]Section "InputDevice"
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        Option          "SendCoreEvents"        "true"
        Option          "Device"                "/dev/psaux"
        Option          "Protocol"              "auto-dev"
        Option          "HorizScrollDelta"      "0"
        Option          "SHMConfig"             "on"
EndSection[/INDENT]
[/COLOR][/SIZE]

And replaced (further down the page):
[SIZE="2"][COLOR="Blue"][INDENT]InputDevice	"Configured Mouse"[/INDENT][/COLOR]
[/SIZE]
With:
[SIZE="2"][COLOR="Blue"][INDENT]InputDevice	"Synaptics Touchpad"[/INDENT]
[/COLOR]
[/SIZE]
After the file was saved I finally used the Terminal to input these commands:
[SIZE="2"][COLOR="Blue"][INDENT]# sudo synclient TapButton1=0 TapButton2=0 TapButton3=0
# sudo synclient RTCornerButton=0 RBCornerButton=0[/INDENT][/COLOR][/SIZE]


Also, changing this seems to have some of the mouse's "wonkiness", but it's movement still isn't even close to OS X, or even WinXP.

[CENTER]-----------------------------------------------------------------------

[SIZE="1"]HOW TO FIX TRACKPAD TAP UBUNTU DAPPER DRAKE COMPAQ LAPTOP NOTEBOOK
HOW TO FIX TRACKPAD TAPPING UBUNTU DAPPER DRAKE COMPAQ LAPTOP NOTEBOOK
HOW TO DISABLE TRACKPAD TAP UBUNTU DAPPER DRAKE COMPAQ LAPTOP NOTEBOOK
HOW TO DISABLE TRACKPAD TAPPING UBUNTU DAPPER DRAKE COMPAQ LAPTOP NOTEBOOK[/SIZE][/CENTER]

---

