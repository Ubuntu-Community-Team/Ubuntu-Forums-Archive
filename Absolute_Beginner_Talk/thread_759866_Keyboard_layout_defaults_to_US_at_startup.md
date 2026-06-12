---
title: "Keyboard layout defaults to US at startup"
date: 2008-04-19
forum: Absolute Beginner Talk
---

### Post by bwallum on 2008-04-19
Old problem returns.

A recent upgrade has changed my keyboard layout from GB to US. If I change it through System>Preferences>Keyboard the layout is ok until I re boot. It then returns to US. This means the changes made are not written to the xorg.conf file.

To fix you need to change the xorg.conf file as follows.

Open a terminal with Applications>Accessories>Terminal. Then copy in this code:

```
gksudo gedit /etc/X11/xorg.conf
```
You will need to type in your administrator password when prompted.

When the file opens find this section:

> Section "InputDevice"
	  Identifier  	"Generic Keyboard"
	  Driver		"kbd"
	  Option		"XkbRules"	"xorg"
	  Option		"XkbModel"	"pc105"
	  Option		"XkbLayout"	"us"
EndSection

Change the "XkbLayout" option to your desired keyboard layout. I'm from Scotland so my code is "gb". The section should now look like this:

> Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"gb"
EndSection

Save and close terminal window. End of irritation. Note that the xorg.conf file will probably show as tabbed entries and not look as compact as quoted above. This is normal.

---

### Post by asgard_command on 2008-04-22
Thanks for this I didn't realise hardy had changed my layout till I tried to type an email and had no at sign.

---

