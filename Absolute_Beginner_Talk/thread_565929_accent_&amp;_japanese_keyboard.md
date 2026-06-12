---
title: "accent &amp; japanese keyboard"
date: 2007-10-02
forum: Absolute Beginner Talk
---

### Post by kenjil on 2007-10-02
Hi folks.
I've just installed xubuntu 6.10 on a japanese laptop.
Everything seems to work well except a crucial detail :
Since I'm half french and half japanese i'd like to type some french accent as well.
Here i encounter a problem. Untill now, most keyboards i've used produce an "é" by
typing "alt"+"acute" and "e". But i can't do this with my settings :

Section "InputDevice"
Identifier "Generic Keyboard"
Driver "kbd"	
Option	 "CoreKeyboard"
Option	 "XkbRules"	"xorg"
Option	 "XkbModel"	"jp106"
Option	 "XkbLayout"	"jp(latin)"
Option	 "XkbOptions"	"grp:ctrl_shift_toggle,lv3:ralt_switch,grp_led:scroll"
Option	 "XkbVariant" "latin,"
EndSection

Anyone can help solving this ?
Thanks, Kenji

---

### Post by shirilover on 2007-10-03
Go to System->Preferences->Keyboard
then click the Layout Options tab.
Expand the tree for Compose key position.
Select one of the options listed and Close.

Then for accent acute, compose key + ' + e -> é
accent grave, compose key + ` + e -> è
&#31777;&#21336;&#12288;&#12391;&#12377;&#12397;&#12290;

---

### Post by kenjil on 2007-10-03
thanks.
I end up choosing another solution.
Since yours would use a 4 keys combination to get an accented letter.
Since i'm not using the katakana layout keyboard i decided to change it into a
an "accent type"

So i changed the file /etc/X11/xkb/symbols/jp
changing for example
key <AD03> { [ kana_I, kana_i ] }
to
key <AD03> { [ dead_acute ] }

and i change the left windows key into a keysymboles group switch mode by adding
in file /etx/X11/xorg.conf
an xkbOptions
grp:lwin_switch

This does what i wanted : to have an accented "é" with a three keys combination, in my case
"lwin" + "e" = accent acute  and "e" to get "é"

À bientôt, Kenji

---

