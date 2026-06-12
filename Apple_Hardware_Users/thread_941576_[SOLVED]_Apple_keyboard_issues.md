---
title: "[SOLVED] Apple keyboard issues"
date: 2008-10-08
forum: Apple Hardware Users
---

### Post by thenes on 2008-10-08
Hi

I have some issues with my white apple keyboard from early 2007, which is in Norwegian.

By default in system -> keyboard Norway Macintosh - eliminate dead keys is used with the model Generic 105-key (Intl) PC. 

This works all right, but does not allow me to use characters where I have to use the right option button. I miss out on characters like ~ and \ .

When I choose keyboard Norway Macintosh still under model Generic 105-key (Intl) PC, my keyboard works like I want it too, including the right option button.

The problem is that if I change my keyboard to Norway Macintosh and remove Norway Macintosh - eliminate dead keys, and then reboot my system, system -> keyboard will once again show Norway  Macintosh - eliminate dead keys. The change does not survive the reboot.

On the other hand, if I add Norway Macintosh in addition to Norway Macintosh - eliminate dead keys, and reboot my system, my keyboard will type strange characters at all of the strokes I give it. When I do this and change back to Norway Macintosh - eliminate dead keys, that option works as it should, but I have to add Norway Macintosh over again to be able to use the right option key.

My xorg.config reads:
> Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"no"
	Option		"XkbVariant"	"mac"
#	Option		"XkbVariant"	"mac_nodeadkeys"
(...)

I replaced the line in that now has the hash with the line that reads Option "XkbVariant" "mac" . This gives me ? in terminal when I try to use the right option key, where the "mac_nodeadkeys" gives me nothing.

I hope somebody can give me a hint in the right direction. Thanks for reading.

---

### Post by thenes on 2008-10-13
I got around the problem today;

I updated my xorg.config using: > sudo dpkg-reconfigure -phigh xserver-xorg

It came out looking like this:
> Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"no"
	Option		"XkbOptions"	"lv3:ralt_switch"


Following the last line I added this line:
> 	Option		"XkbVariant"	"mac"


When I rebooted, the keyboard worked like I want it too, including use of the right option key.

---

