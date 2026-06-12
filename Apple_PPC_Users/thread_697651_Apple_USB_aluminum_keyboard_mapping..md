---
title: "Apple USB aluminum keyboard mapping."
date: 2008-02-15
forum: Apple PPC Users
---

### Post by casbahdk on 2008-02-15
Does anyone have any tips or a HowTo on mapping the new Apple USB aluminum keyboard so that all the keys can be used? I have a Danish version of the keyboard and am having problems getting a "@" and getting rid of dead keys. "@" uses the apostrophe key in combination with the option key.

---

### Post by stream303 on 2008-02-16
Have you tried adding the danish keyboard to your /etc/X11/xorg.conf:
(sudo nano, or gksudo gedit to edit)

```
Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	#Option		"XkbLayout"	"us"
        Option          "XkbLayout"     "dk"
EndSection

```

I just commented out the us keyboard as an example...

---

### Post by casbahdk on 2008-02-16
> **stream303 said:**
> Have you tried adding the danish keyboard to your /etc/X11/xorg.conf:
(sudo nano, or gksudo gedit to edit)

```
Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	#Option		"XkbLayout"	"us"
        Option          "XkbLayout"     "dk"
EndSection

```

I just commented out the us keyboard as an example...

Yes, I just checked. The keyboard had been correctly configured when I installed Gutsy. I guess I will have to roll my own mappings to get the extra stuff to work?

---

