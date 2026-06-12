---
title: "Unable to set the left win key for compose in xorg.conf"
date: 2006-12-31
forum: Absolute Beginner Talk
---

### Post by renraw on 2006-12-31
Hello everybody,

I would like to assign my left windows key on my laptop to act as the compose key. This in order to create characters like the e with umlaut (&euml;), euro (&euro;) and others.

I am aware of the possibilities to use xmodmap, but I would like to use the system wide option with xorg.conf. ```
Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "us"
        Option          "XkbOptions"    "compose:rwin"
EndSection

```

Other options for rwin I have found so far are caps, menu, ralt and rctrl, however using win, lwin, super, super_l do not work.

I have been looking in /etc/X11/xkb/rules and the files xorg, xorg.lst and xorg.xml and altered these manually to also contain a reference to lwin. Using this and the following command resulting in the accompanying error:```
warner@obk:/etc/X11/xkb/rules$ setxkbmap -option compose:lwin
Error loading new keyboard description
```

So, if anybody could help, I am at a complete loss here.

Thank you in advance.

Warner

---

### Post by fimblo on 2007-01-03
I'd really like to know about how to fix this as well. Irritates me that I have a dead key on my keyboard.

thanks

---

