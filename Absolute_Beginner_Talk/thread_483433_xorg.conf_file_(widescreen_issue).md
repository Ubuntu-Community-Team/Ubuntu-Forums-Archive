---
title: "xorg.conf file? (widescreen issue)"
date: 2007-06-24
forum: Absolute Beginner Talk
---

### Post by someguy91 on 2007-06-24
I´ve searched around the forums.. i dont know how to edit the xorg.conf file to get widescreen resolutions on an ATI card? i´m on restricted drivers right now... but no widescreen

---

### Post by BobCFC on 2007-06-24
You have to be root to edit that file such as
```

sudo gedit /etc/X11/xorg.conf
```

The FIRST THING I would do is make a copy of this file for BACKUP.

look for a Display section at the bottom it will say something like

```
SubSection     "Display"
        Depth       24
        Modes      "1280x1024" "1024x768" "800x600" "640x480"
EndSubSection

```

It tries the left-most mode first so you could try adding a mode there such as

```

SubSection     "Display"
        Depth       24
        Modes      "1680x1050" "1280x1024" "1024x768" "800x600" "640x480"
EndSubSection
```

save the file and restart X with Crtl-Alt-Backspace... If it doesn't select it look in System->Preferences->Screen Resolution to see if you can pick it from the list.

---

### Post by someguy91 on 2007-06-24
ok slight problem.. when i pull up the file... nothing is written in there... does that mean I have to get "xorg"?

---

### Post by BobCFC on 2007-06-24
No it sounds like a typo.  It's creating a new file because it cant find the name you gave it.

You can copy&paste to terminal using the right-click menu

---

### Post by Nekiruhs on 2007-06-24
> **BobCFC said:**
> You have to be root to edit that file such as
```

sudo gedit /etc/X11/xorg.conf
```

The FIRST THING I would do is make a copy of this file for BACKUP.

look for a Display section at the bottom it will say something like

```
SubSection     "Display"
        Depth       24
        Modes      "1280x1024" "1024x768" "800x600" "640x480"
EndSubSection

```

It tries the left-most mode first so you could try adding a mode there such as

```

SubSection     "Display"
        Depth       24
        Modes      "1680x1050" "1280x1024" "1024x768" "800x600" "640x480"
EndSubSection
```

save the file and restart X with Crtl-Alt-Backspace... If it doesn't select it look in System->Preferences->Screen Resolution to see if you can pick it from the list.
PLEASE. Use gksudo instead of sudo. It seems small, but sudo is meant for terminal programs like apt-get or nano. gksudo is for graphical programs. I don't feel like explaining a long story, but I lost sudo privelages by doing that and had to go into recovery mode to fix it. Just use gksudo to be safe.

---

### Post by BobCFC on 2007-06-24
Good point.  I don't use gedit myself but it's easier for examples

---

