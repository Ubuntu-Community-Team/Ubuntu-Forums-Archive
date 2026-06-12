---
title: "change keyboard layout on logon screen"
date: 2008-02-17
forum: Absolute Beginner Talk
---

### Post by jontes on 2008-02-17
hi 

im fixing a computer for a friend and when he installed  5.04 on the laptop he was using he had a dvorak setup. Now he has a normal US English setup and we cant change the keyboard layout. Once we logon the keyboard works as a US English keyboard but on the logon screen it stays  dvorak. we hav changed the xorg.conf file from dvorak to us but it still logs on as dvorak and once logged on the computer comes up with an error message saying missing command line unable to run.

any help will be apprecieated thnx

---

### Post by billgoldberg on 2008-02-19
Don't have a clue, but ubuntu is up to 7.10 now.

---

### Post by seventhc on 2008-02-19
I'm not positive, but I would have a look at in your xorg.conf and see if it says dvorak anywhere.
```

gksu gedit /etc/X11/xorg.conf

```my keyboard section reads like this
```

Section "Files"
EndSection

Section "InputDevice"
    Identifier    "Generic Keyboard"
    Driver        "kbd"
    Option        "CoreKeyboard"
    Option        "XkbRules"    "xorg"
    Option        "XkbModel"    "pc105"
    Option        "XkbLayout"    "us"
EndSection

```so you have something to compare it to. I'm not saying to use my settings as I'm not sure if they are specific to my machine or not.

and this too down more in the file.
```

Section "ServerLayout"
    Identifier    "Default Layout"
    Screen        "Default Screen"
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"

```
But just look for the word 'dvorak' anywhere in the file.

---

