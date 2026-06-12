---
title: "Access Denied"
date: 2006-03-25
forum: Absolute Beginner Talk
---

### Post by morwyn on 2006-03-25
I tried to copy a wallpaper i found to the wallpaper folder, but it said access denied. do i have to do it from the terminal? and if so, what commands do i need to use?

---

### Post by trent dillman on 2006-03-25
```
sudo cp /path/to/your/image.jpg /usr/share/backgrounds/
```

---

### Post by Madpilot on 2006-03-25
You don't actually need to move your wallpapers to /usr/share/backgrounds/

When you right-click on your desktop & choose Change Desktop Background, the "Add Wallpaper" button will take them from any directory you care to keep them in and add them to the list.

---

### Post by trent dillman on 2006-03-25
Heh, forgot about that. I guess I figured morwyn wanted it there for some reason unbeknownst to me. :p

---

### Post by Madpilot on 2006-03-25
[https://wiki.ubuntu.com/UbuntuEyeCandy](https://wiki.ubuntu.com/UbuntuEyeCandy) has various bits of information on desktop backgrounds and other visual things.

(This page also needs a better name - "EyeCandy" isn't that clear - any suggestions?)

---

### Post by aysiu on 2006-03-26
You don't have to use the command-line. You can Alt-F2 and ```
gksudo nautilus
``` in Gnome or ```
kdesu konqueror
``` in KDE.

---

