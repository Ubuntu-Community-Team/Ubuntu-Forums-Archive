---
title: "Mouse Touch Sense?"
date: 2008-03-09
forum: Absolute Beginner Talk
---

### Post by Astura on 2008-03-09
How would I set it so to DISABLE MousePad Tapping on my hp laptop?

---

### Post by itix on 2008-03-09
Change *xorg.conf*:
```

gksu gedit /etc/X11/xorg.conf
```
Terminal code ^

go down to the touchpad section which in my *xorg.conf* looks like this:
```
Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
        

```

There you add the folowing line somewhere befor *EndSection*:
```

	Option		"MaxTapTime"		"0"
```

The sudo-password can't be seen while entered so you won't get any stars or dots like in the log-in-screen. Just type it and hit enter.

---

