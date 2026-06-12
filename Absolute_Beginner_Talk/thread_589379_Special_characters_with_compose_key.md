---
title: "Special characters with compose key"
date: 2007-10-24
forum: Absolute Beginner Talk
---

### Post by wkleu on 2007-10-24
Hello

I am having problems setting up my compose key in ubuntu 7.10.
I need it to create special characters like: êë

My right alt (it is marked on my keyboard as "alt gr") is set up as my compose key under System -> Preferences -> Keyboard but it isn't working. I have tried using right ctrl as well but doesn't work either.

It used to work perfectly in 7.04 but it isn't anymore.

I am using a HP Compaq nc8430 notebook and I have tried various keyboard models but without any luck.

Any help will be appreciated.

---

### Post by bapoumba on 2007-10-24
Could you please look in your **/etc/X11/xorg.conf**, in the “InputDevice” section:
```
Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "fr"
        Option          "XkbOptions"    "lv3:ralt_switch, compose:lwin"
```
Here, my left win key is set up as compose.

In **/usr/share/X11/xkb/rules/xorg.lst**, you can find the default keys that can be defined as “compose”:
```
 Compose key          Compose key position
  compose:ralt         Right Alt is Compose.
  compose:lwin         Left Win-key is Compose.
  compose:rwin         Right Win-key is Compose.
  compose:menu         Menu is Compose.
  compose:rctrl        Right Ctrl is Compose.
  compose:caps         Caps Lock is Compose.
```

---

