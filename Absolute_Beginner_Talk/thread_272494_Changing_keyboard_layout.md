---
title: "Changing keyboard layout"
date: 2006-10-06
forum: Absolute Beginner Talk
---

### Post by ianhaycox on 2006-10-06
I installed Ubuntu using my existing French AZERTY keyboard layout some time ago but have recently changed to a UK QWERTY keyboard layout.

I changed the setting in System, Preferences, Keyboard under the layout tab from French to UK and the correct mappings work once logged in.

The problem is during the login screen Ubuntu still thinks I have a French keyboard, so typing my Username and Password is difficult because many of the key mappings are wrong. E.g. typing Ian comes out as Iqn ! Makes it a bit tricky for password entry.

How do I change the 'System wide' default keyboard mapping ?

Thanks,

Ian

---

### Post by NESFreak on 2006-10-06
```
sudo gedit /etc/X11/xorg.conf
```

search for ```
Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
```

and add/change the lines```
	Option		"XkbModel"	"pc104"
	Option		"XkbLayout"	"us"
	Option		"XkbVariant"	"intl"
```

where 	Option		"XkbVariant"	"intl" is for dead keys like " and ~ and stuff

NESFreak

---

### Post by ianhaycox on 2006-10-08
Thanks that worked a treat.

Changed 

        Option          "XkbLayout"     "fr"
to 

        Option          "XkbLayout"     "gb"

but after a XServer restart it still did not work and I got a Gnome warning about my X and Gnome keyboard settings being different. Once I removed the line,

        Option          "XkbVariant"    "latin9"

it worked OK after another XServer restart. So all is well.

---

