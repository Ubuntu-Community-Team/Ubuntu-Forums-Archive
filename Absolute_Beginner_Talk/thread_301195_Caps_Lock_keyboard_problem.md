---
title: "Caps Lock keyboard problem"
date: 2006-11-16
forum: Absolute Beginner Talk
---

### Post by nickpaton on 2006-11-16
HP nx6125 laptop
Edgy 6.10

Discovered that Caps lock doesn't work.

When making changes via system>Preferences>keyboard>layout Options>Caps Lock behaviour, if I select any setting, I get the following error message:

> Error activating XKB configuration.
It can happen under various circumstances:
- a bug in libxklavier library
- a bug in X server (xkbcomp, xmodmap utilities)
- X server with incompatible libxkbfile implementation

X server version data:
The X.Org Foundation
70101000

If you report this situation as a bug, please include:
- The result of xprop -root | grep XKB
- The result of gconftool-2 -R /desktop/gnome/peripherals/keyboard/kbd

Any Idea?  Is this actually a reportable bug?

---

### Post by kmbrow on 2006-12-25
Don't know if you solved your problem or not but I've been having the same issue and managed to correct it.

All I did was open xorg.conf and change one option in the Input Device section from

```
Option		"XkbLayout"	"uk"
```


to

```
Option		"XkbLayout"	"gb"
```

This fixed the Caps Lock problem and also got rid of the error messages when using System --> Preferences --> Keyboard.
This may not work for you as it depends on what keyboard layout you're using, but then again it might ...

Regards
Kevin

---

### Post by nickpaton on 2006-12-29
Thanks Kevin

I've since done a reinstall, so difficult to say!!  But I'll keep this archived for future use.

---

### Post by case1976 on 2006-12-30
Yes, i had the same problem with Edgy (i returned to Dapper therefore). So strange that caps lock refused to work on Edgy. My machine is intel pentium 3, i used the xubuntu 6.10 cd-image for installation.

---

### Post by case1976 on 2007-02-19
I have to correct now my previous post! After the latest february kernel update, caps lock started to work quite correctly on Edgy on my comp. Thats great! 
Dapper is noticeably slower, in comparison with Edgy, i have to admit. :)

---

