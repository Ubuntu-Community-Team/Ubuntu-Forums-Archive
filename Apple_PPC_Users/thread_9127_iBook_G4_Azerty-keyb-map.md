---
title: "iBook G4 Azerty-keyb-map?"
date: 2004-12-24
forum: Apple PPC Users
---

### Post by mistic on 2004-12-24
hi, i've just installed Ubuntu on my baby (a G4 iBook 12") and everything seems to be working fine, except for one small thing...

my keyboard aint fully working yet...

its an azerty-keyboard but the belgian-lay-out aint working really well since the "at" and the little square-thingy (cant type them atm) are on the ²-³-button, also i don't have the 'pipe'-key wich is also kind of a nag...

anyone an idea on how to fix it? or where i can find the right keymap?

---

### Post by mistic on 2004-12-24
i found the solution :-)

there's an fr_new-keymap floating around the web that seems to be doing the trick...

[http://seb.france.free.fr/linux/ibookG4/fr_new](http://seb.france.free.fr/linux/ibookG4/fr_new)

just put that file here

```
/usr/X11R6/lib/X11/xkb/symbols/macintosh/fr_new

```
and add this to your /etc/X11/XF86Config-4:

```
Section "InputDevice"
       Identifier      "..."
       Driver          "Keyboard"
       Option "Protocol"       "Standard"
       Option "AutoRepeat"     "250 30"
       Option "LeftAlt"        "Meta"
       Option "RightAlt"       "Meta"
       Option "ScrollLock"     "Compose"
       Option "RightCtl"       "Control"

       Option "XkbLayout"     "macintosh/fr_new"
EndSection
```

this did the trick for me...

---

### Post by mistic on 2004-12-24
[http://seb.france.free.fr/linux/ibookG4/iBookG4-howto-5.html#ss5.4](http://seb.france.free.fr/linux/ibookG4/iBookG4-howto-5.html#ss5.4)

=> that's the info-link should you need it :-)

its actually a great howto on how to get debian (and thus in a way ubuntu too) running on an iBook

grtz
Mistic

---

### Post by micky501 on 2005-01-10
Hi,

I have tried your solution but it doesn't work on my computer.. When I do exactly what you say, my X server crashes and I must re-write the /etc/X11/XF86Config-4 file..

It seems that some problems appear with the xkb component. Any idea ??

My configuration is a iBook G3 and I run the latest version of Ubuntu-Warty

Thks
Micky from Rennes, France

---

### Post by mistic on 2005-01-11
what error message does it spawn?

did you put the keymap in the right place?

if yes to both of the above:

try modifying you config like this:

```
Section "InputDevice"
    Identifier  "Generic Keyboard"
    Driver      "keyboard"
    Option      "CoreKeyboard"
    Option      "XkbRules"  "xfree86"
    Option      "XkbModel"  "macintosh"
    Option      "XkbLayout" "fr_new"
EndSection
```

got it from another tutorial about azerty-keymap on ibook and it seems to work here too

if you get it working:
[INDENT]alt + ( = {
alt + ) = }
shift + alt + L = |
shift + alt + N = \
shift +alt + ? = ¿
shift +alt + / = \[/INDENT]

ow yeah and fn + backspace = delete

hope it helps cause i know how mutch it sucks not being able to use the right keys...

I'm not a specialist, but if you need help, let me know and I'll try...

---

### Post by irezumi_x on 2005-06-10
[QUOTE=mistic]and add this to your /etc/X11/XF86Config-4:
[/QUOTE]

I'm fairly new to Linux, but I installed Ubuntu on an iBook g4 too, and installed the XFree86 as described in 5.2 form this page: [http://seb.france.free.fr/linux/ibookG4/iBookG4-howto-5.html](http://seb.france.free.fr/linux/ibookG4/iBookG4-howto-5.html) .
I can't seem to open or edit the XF86Config-4 though? Any suggestions?

---

