---
title: "ibook backspace?"
date: 2006-10-04
forum: Apple PPC Users
---

### Post by movies1978 on 2006-10-04
I did not find anything using the search.
Can anyone tell me where I can find backslash key on an ibook when using ubuntu.

Best regards 
Mathias

---

### Post by imho74 on 2006-10-06
Hi Mathias,

this depends on the key map you are using. When you are using a German, British, American or etc. key map for a PC keyboard, you will find the backslash at the same position where it is on a PC Keyboard. For example: On German PC Keyboards you get the backslash by pressing "Alt Gr" + "ß". I use this key map for my iBook, because there is no Mac-like key map for this keyboard. So I get the backslash by pressing "Apple Key" and "ß", because "Apple Key" acts like the "Alt Gr"-Key on a PC keyboard.  

Regards,
Christian

---

### Post by movies1978 on 2006-10-06
Hi Christian,
I use the german layout, but still the apple + ß does not return any sign. I am little lost here. What keyboard did you choose. Mine is set to Macintosh + eliminate German Dead Keys.
Any further ideas?


Mathias

---

### Post by imho74 on 2006-10-07
Hallo Mathias,

it seems that the German Macintosh key map doesn't work correctly with the keyboard of the iBook. That's the reason why I have choosed the key map of a PC. In my /etc/X11/xorg.conf you can find the following entry for this:
```

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "de"
        Option          "XkbVariant"    "nodeadkeys"
        Option          "XkbOptions"    "lv3:lwin_switch"
EndSection

```

For Gnome I choosed in "Keyboard (Tastatur)" a "Generic 105-key (Intl) PC" key map.

Hope that this is helpful for you.

Regards,
Christian

---

