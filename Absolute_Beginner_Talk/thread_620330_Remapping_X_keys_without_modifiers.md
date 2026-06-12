---
title: "Remapping X keys without modifiers"
date: 2007-11-22
forum: Absolute Beginner Talk
---

### Post by ckth on 2007-11-22
Hello,

I've been trying to find a way to remap keys with [COLOR="DarkRed"][xmodmap]("http://www.xfree86.org/4.2.0/xmodmap.1.html")[/COLOR] to suit my needs.
---------------------------------------------------
1. When typing in Abiword, recalling recent bash commands at the terminal or while writing equations in Lyx, for instance, having to let go of the home keys and travel to the arrow keys to navigate around is time consuming. (Especially when there are thirty equations waiting to be typed!)

How do I remap the h,j,k,l keys in conjunction with ALt_L so that I gain vim like bindings globally? (That is, <Alt_L>+<j> must emulate the down arrow key, <Alt_L>+<k> the up arrow key, and so on.)

The only way I could manage this was to use [COLOR="DarkRed"][Mode_switch]("http://www.linux.com/base/ldp/howto/Keyboard-and-Console-HOWTO-13.html")[/COLOR] :

Defining Alt_L to be Mode_switch:
```
xmodmap -e "keysym Alt_L = Mode_switch"
```

and setting:
```
xmodmap -e "keycode 44 = j J Down"
xmodmap -e "keycode 45 = k K Up"
-and so on-
```

does the job, but this cripples Alt_L, as I can no longer use it to alt-tab between windows, or to switch to VCs.

Is there a clever way of accomplishing this without sacrificing Alt to the Mode_switch keysym? Similar jugglery with the Meta_L and Ctrl_L keys is out of the question, for the same reasons. Gconf editing (if at all relevant) is out of the picture as well, as I spend most of my time away from Gnome.
-----------------------------------------------------
2. Also, is there a way of defining more than one key to the same keycode? That is, I want a way to "alias" Caps_Lock to Escape, to avoid having to reach for the Esc key in vim. 
```
xmodmap -e "remove Lock = Caps_Lock" 
xmodmap -e "keycode 9 = Caps_Lock"
```

assigns the escape function to Caps_Lock- but Escape can no longer be used. 
Mentioning one after the other-
```
xmodmap -e "keycode 9 = Caps_Lock Escape
```

Activates escape only when the shift key is held down.
-------------------------------------------------------

I've been using linux for about an year now, but this is the first time I couldn't find instructions for a tweak I needed on the internet, so I'm being forced to post- I hope I've followed all posting guidelines correctly.

---

### Post by ckth on 2007-12-27
Solved. 

Had to dig up xkbcomp tutorials and documentation, and it took me well over a month, but I finally figured it can't be done with xmodmap.

Here's the final code:

```
xkb_keymap {
  xkb_keycodes  { include "xfree86+aliases(qwerty)" };
  xkb_types     { include "complete"      };
  xkb_compat    { include "complete"      };
  xkb_symbols   {
    include "pc(pc105)"

    key <CAPS> { type[Group1] = "ONE_LEVEL", symbols[Group1] = [ ISO_Level3_Shift ] };
    key <AC06> {	[	  h,	H, 	Left,	G		]	};
    key <AC07> {	[	  j,	J,	Down,	F		]	};
    key <AC08> {	[	  k,	K,	Up,	D		]	};
    key <AC09> {	[	  l,	L,	Right,	S		]	};
 
    };
  xkb_geometry  { include "pc(pc104)"     };
};
```

Which I have to get X to run as it starts, with:

```
xkbcomp changekeys.xkb $DISPLAY 2 > /dev/null
```

(Capslock is the new modifier, and holding Caps down gives me vim like key bindings for the h,j,k and l keys.) 
If only things didn't take months to figure out alone on Linux. :(

---

