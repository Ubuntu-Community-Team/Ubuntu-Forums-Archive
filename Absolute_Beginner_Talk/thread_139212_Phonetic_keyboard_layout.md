---
title: "Phonetic keyboard layout"
date: 2006-03-03
forum: Absolute Beginner Talk
---

### Post by Zdravko on 2006-03-03
Do you know how to get a phonetic keyboard layout on Ubuntu? I want to type in phonetic cyrilic, but it doesn't work. Here is my xorg.conf:
> 
Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us,de,bg"
	Option 		"XkbVariant" 	",phonetic"
	Option		"XkbOptions"	"grp:alt_shift_toggle"
EndSection

With these settings I get an error message after restart because of some X incompatibility. No phonetic works :(

---

### Post by Brunellus on 2006-03-03
this should probably not be necessary.  Are you working in GNOME?  Gnome has a Keymap switcher applet which works fine.  I use it to switch between En-US and Spanish keymaps.

---

