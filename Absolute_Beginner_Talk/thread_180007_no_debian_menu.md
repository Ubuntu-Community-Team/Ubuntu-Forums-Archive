---
title: "no debian menu"
date: 2006-05-21
forum: Absolute Beginner Talk
---

### Post by mannock on 2006-05-21
i find that after installing some applications,  they aren't listed in the menu so i end up having to find them in the file system and creating shortcuts to run them.  so i installed menu-xdg   but even that won't show in any menu lists.
then i installed  menu  but no sign of that either.:(

---

### Post by S{yndrom}e on 2006-05-21
try doing this command in terminal

sudo killall gnome-panel 

I am assuming you are using ubuntu not kubuntu.

This should refresh the Gnome Panel, displaying newly added icons hopefully.

---

### Post by tseliot on 2006-05-21
try with:
```
sudo update-menus
```

Then log out and press CTRL+ALT+Backspace

Then log in

---

### Post by S{yndrom}e on 2006-05-21
that also works =P

---

### Post by mannock on 2006-05-21
aha,  the second one did it,   (sudo update-menus)
magic.   thanks.

---

