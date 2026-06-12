---
title: "Problems using Microsoft Wheel Mouse - Ubuntu noob"
date: 2007-04-28
forum: Absolute Beginner Talk
---

### Post by shutrbug on 2007-04-28
I recently installed Feisty (I'm a Linux noob) and have run into a maddening problem that I just can't solve, namely how do I configure the mouse button of my Microsoft Wheel Mouse Optical?  I'm used to pressing the scroll wheel (acts as the middle mouse button) as the "back" key in Firefox to speed up my browsing.  How do I configure this in GNOME/Ubuntu?  I looked at System -> Preferences -> Mouse, but there isn't anything on configuring the buttons other than to switch to a left-handed configuration.:confused: 

Thanks in advance for any advice.  I'm sure it's something simple.

---

### Post by lepz on 2007-04-28
Do a search of the name/model # of your mouse.

---

### Post by shutrbug on 2007-04-28
Well, I did a quite a bit of searching and I guess I can't remap the middle button to do what I want, at least not easily.  I did find out how to remap the middle mouse button in Firefox with about:config to keep it from performing the usual cut/paste function, but I can't figure out how to remap it to back.:(

---

### Post by HotrodChev on 2007-06-04
I just went through the same problem as you. I took me a while to figure it out. I had to edit my /etc/X11/xorg.conf file.

Try in terminal:

sudo gedit /etc/X11/xorg.conf

to edit your file. Look for the section in there that closely matches the section below and edit your file to match mine. This is for a M$ wheel mouse optical (has a right and left button , a wheel that is click able as a third button) basic mouse.

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option "Device" "/dev/input/mice"
	Option "Protocol" "ExplorerPS/2"
	Option "Buttons" "7"
	Option "Emulate3Buttons"	"true"
	Option "ButtonMapping" "1 6 3 2 7"
	Option "ZAxisMapping"	"4 5"
	Option "Resolution" "100"
EndSection

Save the file and reboot. Hopefully it will work for you.

---

