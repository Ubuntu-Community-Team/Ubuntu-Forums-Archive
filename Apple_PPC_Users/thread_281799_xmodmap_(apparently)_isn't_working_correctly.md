---
title: "xmodmap (apparently) isn't working correctly"
date: 2006-10-21
forum: Apple PPC Users
---

### Post by nmsb on 2006-10-21
Hi!

I have an iBook (late 2004) with a portuguese keyboard and finally decided to make the keyboard work correctly...

To start here is the output of "setxkbmap -print".


nmsb@mediterraneo:~$ setxkbmap -print
xkb_keymap {
        xkb_keycodes  { include "xfree86+aliases(qwerty)"       };
        xkb_types     { include "complete"      };
        xkb_compat    { include "complete"      };
        xkb_symbols   { include "pc(pc105)+pt"  };
        xkb_geometry  { include "pc(pc105)"     };
};


Even though this is an iBook, the Generic 105-key (Intl) PC with portuguese layout was the best option :-|

To remap the keyboad I issued the following commands:


nmsb@mediterraneo:~$ xmodmap -pke > .xmodmap-mediterraneo.original
nmsb@mediterraneo:~$ cp .xmodmap-mediterraneo.original .xmodmap-mediterraneo


and then edited the file ".xmodmap-mediterraneo", using "xev" to find out which keycodes to change. After the editing, here are the differences:


nmsb@mediterraneo:~$ diff .xmodmap-mediterraneo .xmodmap-mediterraneo.original
5c5
< keycode 12 = 3 numbersign EuroSign sterling sterling sterling
---
> keycode 12 = 3 numbersign sterling sterling sterling sterling
14c14
< keycode 21 = plus asterisk dead_diaeresis dead_ogonek dead_cedilla dead_ogonek
---
> keycode 21 = guillemotleft guillemotright dead_cedilla dead_ogonek dead_cedilla dead_ogonek
27c27
< keycode 34 = masculine ordfeminine asterisk dead_diaeresis dead_abovering dead_diaeresis dead_abovering
---
> keycode 34 = plus asterisk dead_diaeresis dead_abovering dead_diaeresis dead_abovering
41,42c41,42
< keycode 48 = dead_tilde dead_circumflex dead_circumflex dead_caron dead_circumflex dead_caron
< keycode 49 = section plusminus notsign notsign notsign notsign
---
> keycode 48 = masculine ordfeminine dead_circumflex dead_caron dead_circumflex dead_caron
> keycode 49 = backslash bar notsign notsign notsign notsign
44c44
< keycode 51 = backslash bar dead_grave dead_breve dead_grave dead_breve
---
> keycode 51 = dead_tilde dead_circumflex dead_grave dead_breve dead_grave dead_breve
108c108
< keycode 115 = ISO_Level3_Shift
---
> keycode 115 = Super_L


Changes done, I load the keyboard using


nmsb@mediterraneo:~$ xmodmap .xmodmap-mediterraneo


and everything is almost working as it should.  Because of the "almost working as it should", I reboot the computer and make sure that the new ".xmodmap-mediterraneo" is loaded, but the problems remain.

Now the problems :-(

* Pressing simultaneously the TLC, read the Third Level Chooser, (keycode 115 just above) and 3 (keycode 12 at the beginning of the diff) I should be able to write € (EuroSign), right?  Wrong!  The £ (sterling) character is written instead of €.  (I am able to write @ using simultaneously the TCL and 2 (keycode 11), as it should be on this keyboard.)

* Pressing simultaneously the TCL and + (keycode 21) and the the space I should be able to write " (dead diaeresis), right?  Once more wrong, I get a cedil?!?

* The dead_diaeresis problem also unables me to use, e.g., an u with diaeresis.  (OK, in portuguese nobody needs diaeresis, but I've studied german...  Anyhow, even if I hadn't studied german, I should be able to use them!)

Could someone help me?  What am I doing wrong?

PS - I know this is not the best solution as the keyboard at login (still) has some characters in the wrong places (and I've got to choose my passwords a lit bit more carefully :-), but after login everything should be right.

---

