---
title: "&quot;|&quot; pipe character on Dell D620"
date: 2007-11-29
forum: Absolute Beginner Talk
---

### Post by DigitalisCZ on 2007-11-29
I have made fresh install of 7.10 on Dell D620. Most of things works just fine but I cannot type "|" (pipe character). It gets a real bottleneck in my learning of Bash.... Also backslash does not come easily but at least it works with Right Alt+\

I am using US. English and Czechia Qwerty keyboard and I have tried few other keyboard layouts/models with no success. Browsing other posts and forums did not help either.

In terminal (after pressing Ctr-Alt-Fx) the pipe and backlash type correctly so I assume my HW is working properly. However I noticed I cannot type tilda "~" character in there... but this a smaller issue than the pipe one.

My xorg.config
```
Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
	Option		"XkbVariant"	"alt-intl"
	Option		"XkbOptions"	"lv3:ralt_switch"
EndSection
```

Thank you for any ideas.

---

### Post by eolson on 2007-11-29
Don't know if this will work on your system or not,  but

Generic 104 Key PC
U.S. English

works fine on my Dell 530.

---

### Post by DigitalisCZ on 2007-11-29
I tried but it does not changed anything. I reckon this is rather setup than HW dependent problem.

---

### Post by DigitalisCZ on 2007-12-02
I have finally read enough about to dare to edit config files. Apparently there is no definition for backslash/pipe key in US keyboard layout (a bug?).


```
sudo gedit /etc/X11/xkb/symbols/us
```

add following  line to the section xkbd_symbols "basic"

```
 key <BKSL> { [ backslash,        bar,       notsign,        brokenbar ] };
```

---

