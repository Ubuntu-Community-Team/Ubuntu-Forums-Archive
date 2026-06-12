---
title: "switching keyboard layout in xubuntu"
date: 2006-10-09
forum: Absolute Beginner Talk
---

### Post by prattler on 2006-10-09
Hello, I would like to be able to switch keyboard layouts with alt+shift or any other combination. Didn't find any such setting in xubuntu.

I had most success following [this thread]("http://www.ubuntuforums.org/showthread.php?t=63759"), but still couldn't make alt+tab so simply switch.

Thanks for help!

---

### Post by apkolev on 2006-10-10
Hi! 

I had the same problem but look what I found:

[The XKB Configuration Guide]("http://xfree86.org/current/XKB-Config.html")

It is working perfect with 3 layouts for me and alt+shift is working. 

Here is how my xorg.conf looks like:

> Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc104"
	Option		"XkbLayout"	"us,bg,se"
	Option 		"XkbVariant" 	",phonetic,"
	Option 		"XKbOptions" 	"grp:alt_shift_toggle"

EndSection


This allows me to use US, Bulgarian (Phonetic) and Swedish keyboard layouts. Read the webpage for more information.

It is strange though because alt+shift is working only if I select another layout with the mouse and then with alt+shift can switch back to default. Once I am at the default (us for me) it is not working. I have no idea why.

---

