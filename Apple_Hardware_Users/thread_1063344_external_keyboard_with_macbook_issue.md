---
title: "external keyboard with macbook issue"
date: 2009-02-07
forum: Apple Hardware Users
---

### Post by rifak on 2009-02-07
hey everyone,

i just bought an external wireless keyboard tonight and it worked perfect when i plugged it in and still works great. but the problem is that when i unplug it, my macbook keyboard will not work. i am only able to type numbers (like a number pad with j=1,k=2,u=4...) and the pommed keys work also (volume, brightness). i posted the keyboard bit of my xorg:

---------
Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
	Option		"XkbVariant"	"mac"
	Option		"XkbOptions"	"lv3:ralt_switch"
EndSection
---------

it seems as if it didn't change anything in the xorg. and one last thing, when i log out, i can type fine in the logout screen with the macbook keyboard, but as soon as gnome loads, the mac keyboard goes back to not working. any help with this would be awesome. thanks everyone!

---

### Post by Gen2ly on 2009-02-08
geesh.  xorg is going to hal for device recognition.  tryputting 

```
Option          "XkbLayout"             "evdev-managed keyboard"
```

in you xorg.conf.  make sure to comment the other one out and see if it does the trick.

---

### Post by rifak on 2009-02-08
hey thanks for the help. unfortunately it didnt work..it just threw me into safe graphics mode and still no macbook keyboard. what is weird though is that when i logoff and log back on, i get an error message saying:

----------
Error activating XKB configuration.
It can happen under various circumstances:
- a bug in libxklavier library
- a bug in X server (xkbcomp, xmodmap utilities)
- X server with incompatible libxkbfile implementation

X server version data:
The X.Org Foundation
10400090

If you report this situation as a bug, please include:
- The result of xprop -root | grep XKB
- The result of gconftool-2 -R /desktop/gnome/peripherals/keyboard/kbd
----------------

this happened before i tried the fix you suggested, so it wasnt what you had told me to do. so just to make sure what i did was right: i replaced the "Option.."xkblayout"..."us"" part with the "evev..." part. if this is right, it didnt work. thanks for the help though. if anything else, please let me know. this pretty much turns my laptop into a desktop since i cant use the laptop keyboard anymore haha good thing i still have osx on there

---

### Post by rifak on 2009-02-08
so this is weird...after using my mac partition for a night, i logged back into ubuntu and my keyboard was working again?? hmmmm. did mac load something at startup for linux to recognize both keyboards? any input would help. but yeah, both keyboards are working now.

also, in my previous post, i posted an error message that appears at startup/login..does anyone know how to resolve that error (or at least remove the message when i log in). thanks for the help.

---

### Post by cyberdork33 on 2009-02-09
See this bug for the layout errors:
[https://bugs.launchpad.net/bugs/67188](https://bugs.launchpad.net/bugs/67188)

---

### Post by rifak on 2009-02-09
well the issue is fixed. i fixed it by opening Keyboard Preferences and going to the Layouts tab. Under the Keyboard Model dropdown list, I chose Apple Laptop. I also deselected the default circle for the USA Macintosh layout. I'm guessing that my wireless keyboard changed the USA Macintosh layout to default and that's what was throwing up the kbd and xkb error.

---

### Post by cyberdork33 on 2009-02-09
> **switham said:**
> well the issue is fixed. i fixed it by opening Keyboard Preferences and going to the Layouts tab. Under the Keyboard Model dropdown list, I chose Apple Laptop. I also deselected the default circle for the USA Macintosh layout. I'm guessing that my wireless keyboard changed the USA Macintosh layout to default and that's what was throwing up the kbd and xkb error.
The Macintosh Layout is what you are 'supposed' to use, but there are some bugs...

---

### Post by rifak on 2009-02-09
> **cyberdork33 said:**
> The Macintosh Layout is what you are 'supposed' to use, but there are some bugs...

Yeah, I tried to change it back to the Macintosh layout, but it gives me an error so I'm sticking with the Apple layout. Oh well, I don't see any change with that so we'll see how that works out. Thanks for the input!

---

