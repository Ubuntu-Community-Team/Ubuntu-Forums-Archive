---
title: "Keyboard broken in X in Edgy (iBook G3)"
date: 2007-02-20
forum: Apple PPC Users
---

### Post by maggot_brain on 2007-02-20
Hello all,

for some reason Edgy doesn't work with the macintosh keymap in X.  It works in Debian Etch but not in Edgy.  I'm using a UK iBook G3.  I'm thinking of switching from Debian to Ubuntu.  How much longer will there be Ubuntu PPC releases? Any help would be appreciated.  Here's the relevant xorg.conf section that works in Debian Etch but not Ubuntu Edgy

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"macintosh"
	Option		"XkbLayout"	"gb"
EndSection

thanks,

Ananda

---

