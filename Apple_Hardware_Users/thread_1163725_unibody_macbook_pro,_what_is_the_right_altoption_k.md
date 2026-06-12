---
title: "unibody macbook pro, what is the right alt/option key?"
date: 2009-05-19
forum: Apple Hardware Users
---

### Post by inphektion on 2009-05-19
In my dell windows computer there was an alt key on the left side and an alt key on the right.  Came in handy for any alt-whatever keyboard shortcuts, I could do them all with one hand.  Using the right alt key for the letters on the right side and the left alt key for those on the left....

On my macbookpro the left alt key functions as alt.  As in opera a keyboard shortcut to go back is alt-(left arrow).  obviously it would be easier for me to use the right alt since the arrow keys are there but this doesn't work...

so anyone have any insight on what the right alt is and how I can make it function as an alt key like the left one does?

---

### Post by cyberdork33 on 2009-05-19
> **inphektion said:**
> so anyone have any insight on what the right alt is and how I can make it function as an alt key like the left one does?
it may be mapped to alt-gr by default now... This is used to type some special characters. You should be able to use xev to identify the key, and xmodmap to remap it.

---

### Post by inphektion on 2009-05-20
> **cyberdork33 said:**
> it may be mapped to alt-gr by default now... This is used to type some special characters. You should be able to use xev to identify the key, and xmodmap to remap it.

looking at this: 
```
root@nihility:~# xmodmap
xmodmap:  up to 2 keys per modifier, (keycodes in parentheses):

shift       Shift_L (0x32),  Shift_R (0x3e)
lock        Caps_Lock (0x42)
control     Control_L (0x25),  Control_R (0x69)
mod1        Alt_L (0x40),  Meta_L (0xcd)
mod2        Num_Lock (0x4d)
mod3      
mod4        Super_L (0xce),  Hyper_L (0xcf)
mod5        ISO_Level3_Shift (0x5c),  Mode_switch (0xcb)

root@nihility:~# setxkbmap -print
xkb_keymap {
	xkb_keycodes  { include "evdev+aliases(qwerty)"	};
	xkb_types     { include "complete"	};
	xkb_compat    { include "complete"	};
	xkb_symbols   { include "pc+us(mac)+inet(evdev)+level3(ralt_switch)"	};
	xkb_geometry  { include "pc(pc105)"	};

```

am i right in saying it seem xmodmap has the LEFT alt mapped to 0x40 but the RIGHT alt is mapped no where.  So does anyone know how I could use setxkbmap in my .xinit file to map the RIGHT alt to the same as left alt?

---

### Post by cyberdork33 on 2009-05-20
what output do you get in xev when pressing the right ALT key

---

### Post by inphektion on 2009-05-21
the output is: 
```
KeyPress event, serial 34, synthetic NO, window 0x4e00001,
    root 0x13c, subw 0x0, time 755581, (498,-128), root:(501,889),
    state 0x0, keycode 108 (keysym 0xfe03, ISO_Level3_Shift), same_screen YES,
    XKeysymToKeycode returns keycode: 92
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: False

KeyRelease event, serial 34, synthetic NO, window 0x4e00001,
    root 0x13c, subw 0x0, time 755629, (498,-128), root:(501,889),
    state 0x80, keycode 108 (keysym 0xfe03, ISO_Level3_Shift), same_screen YES,
    XKeysymToKeycode returns keycode: 92
    XLookupString gives 0 bytes: 
    XFilterEvent returns: False

```

---

### Post by cyberdork33 on 2009-05-21
OK so it is keycode 108 and is currently assigned to ISO_Level3_Shift

now with xmodmap you want to make 
keycode 108 = Alt_R

[FONT=Verdana]
There is a good how to here:
[http://cweiske.de/howto/xmodmap/allinone.html](http://cweiske.de/howto/xmodmap/allinone.html)
[/FONT]

---

### Post by inphektion on 2009-05-21
perfect.  thanks man.

---

