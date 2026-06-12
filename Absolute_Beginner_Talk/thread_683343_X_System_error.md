---
title: "X System error"
date: 2008-01-30
forum: Absolute Beginner Talk
---

### Post by Nessa on 2008-01-30
I get this everytime I log in. What can I do fix it?

[IMG]http://i115.photobucket.com/albums/n311/jgd0m/pc/error-1.jpg[/IMG]

---

### Post by PurposeOfReason on 2008-01-30
In your /etc/X11/xorg.conf file, look for the keyboard layout and change it from 101 to 105 or vise versa for which one you want to use (change the gnome settings if you want it the other way).

---

### Post by Nessa on 2008-01-30
Is there any difference between the two? Thank you for your quick reply.

---

### Post by LowSky on 2008-01-30
The differnece is the amount of keys, 105 vs 101

i guess your using a differnet sized keyboard...?

```
sudo gedit /etc/X11/xorg.conf
```
find this part and change the 101 to 105 (I highlighted in red)
```

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	[COLOR="Red"]"pc105"[/COLOR]
	Option		"XkbLayout"	"us"
EndSection
```

---

### Post by oedha on 2008-01-30
you can use both...it happend after you installed xserver-xgl
open /etc/X11/xorg.conf  
find this section
Section "InputDevice"
    Identifier    "Generic Keyboard"
    Driver        "kbd"
    Option        "CoreKeyboard"
    Option        "XkbRules"    "xorg"
    Option        "XkbModel"    "pc101"    [COLOR=Red]<------manually change this[/COLOR]
    Option        "XkbLayout"    "us"
EndSection

~E~

---

### Post by Nessa on 2008-01-30
Same keyboad. It was the other way around. I went ahead and changed 105 to 101. Thanks guys! :)

---

