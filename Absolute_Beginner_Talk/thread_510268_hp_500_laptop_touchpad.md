---
title: "hp 500 laptop touchpad"
date: 2007-07-26
forum: Absolute Beginner Talk
---

### Post by fishvetmj on 2007-07-26
Hi. I have been looking on forums for a simple description to the problem of the touchpad on my HP500 not working when I install Ubuntu 7.04. However, the solutions I have found to date either have not worked for me or are written in such a way as to make them difficult to understand. Does anyone out there know where I can get information in a step by step guide for solving this problem? Bear in mind that I am completely new to Linux and Ubuntu and have no experience with programming or code at all!

Many thanks in anticipation. There does seem to be a good description of a solution at [http://www.hexten.net/2007/03/25/tou...-hp-510-ubuntu](http://www.hexten.net/2007/03/25/tou...-hp-510-ubuntu) but this is for version 6.1, and I have no idea if it would apply to 7.04.

---

### Post by Espreon on 2007-07-27
There is but one solution....ditch the big, bad touchpad and get a magical device called a mouse!
And for the link, it may or may not work in Feisty.

---

### Post by anewguy on 2007-07-27
You need to install gsynapics and then add    Option  "SHMConfig"  "true" to the device section of xorg.conf.   If you need help doing that, post back here.:)

---

### Post by fishvetmj on 2007-07-27
Many thanks guys. Anewguy... could you post a complete description of your solution... I'm a complete beginner to this code stuff and don't really know what I'm doing yet!

Many thanks

---

### Post by anewguy on 2007-07-27
No problem, I hope this is good enough!:)

(1) move your mouse cursor to the top bar, click on System, then slide down to Administration, then over and down to and click on Synaptic Package Manager.  BTW - the password it wants is just your login password

(2) when the package manager is fully loaded, click on Search and type "touchpad" in the box, then click the Search button on that window

(3) look for the package called "gsynaptics", click on the box in front of it and click on Install.  The box should now be a green square

(4) click on Apply and let the package install.  When this all completes, exit the package manager

(5) move your mouse cursor to the top bar, click on Applications, then slide down to Accessories, then over to and click on Terminal.  This will open a terminal window where you can put in command lines.

(6) in the terminal window, type  sudo gedit /etc/X11/xorg.conf   .  Again, the password it wants is just your logon password

(7) when the editor starts, click the find button

(8) in the find window, put    touchpad    in the Search for string and click find.  You may have to click find more than once until you find a section that looks something like the following:

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizScrollDelta"	"0"
EndSection


move your mouse cursor down to the very beginning of the EndSection line (before the "E") and press enter to insert a blank line.  Now type this in the blank line:

	Option		"SHMConfig"		"true"


you should now have a section that looks like this:

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizScrollDelta"	"0"
	Option		"SHMConfig"		"true"
EndSection

(9) click on the Save button and exit the editor

(10) close the terminal window

Now you need to log off, wait for the log on window, hold down ctrl alt and press backspace.  This will restart the X server so the change you made to xorg.conf will take effect.

Now just log on.  Look under System/Preferences and you should see an entry now for Touchpad.  Use it to configure your touchpad.:)

I hope this works for your system!  Please post back when you have finished!:)

---

### Post by fishvetmj on 2007-07-28
Many, amny thanks for your time... I have no internet connection at the moment but will try your solution as soon as I can get online. Will let you know how it works out!

Cheers

---

