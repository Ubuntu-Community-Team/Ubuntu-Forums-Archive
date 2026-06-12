---
title: "installed program doesn't show up in menu"
date: 2006-02-11
forum: Absolute Beginner Talk
---

### Post by thort on 2006-02-11
Hi !

I run gnome on Ubuntu 5.10. What could be the cause when an installed program doesn't show up in the menu? This have happened several times. Last failure was when I installed Wine. Everything worked fine in the Synaptic Package Manager. It says the program is installed, but I can't find any icon in the menus. Strange!

---

### Post by taurus on 2006-02-11
I don't have wine running on my machine (see no need for it) so I am not sure exactly if it would add an icon to your menu but you can always run it from a terminal or add it to your top panel (kind like a shortcut)...

---

### Post by d1337 on 2006-02-11
Applications --> System Tools --> Applications Menu Editor

d1337

---

### Post by thort on 2006-02-11
[QUOTE=taurus]I don't have wine running on my machine (see no need for it) so I am not sure exactly if it would add an icon to your menu but you can always run it from a terminal or add it to your top panel (kind like a shortcut)...[/QUOTE]

Thanks!

I'm a newbie. What would be the command to start WIne in the terminal?

---

### Post by thort on 2006-02-11
[QUOTE=d1337]Applications --> System Tools --> Applications Menu Editor

d1337[/QUOTE]

Thanks!

Looked throw Applications Menu Editor. No Wine there.

---

### Post by aysiu on 2006-02-11
Wine doesn't show up in the menus because it's a helper program, not a program that launches by itself.

For example, when I had FileZilla installed with Wine, my launcher for FileZilla was something like this: ```
wine "z:\home\username\.wine\drive_c\Program Files\FileZilla\FileZilla.exe"
``` Wine basically helps you launch a .exe file. Wine can't run by itself.

---

### Post by thort on 2006-02-11
[QUOTE=aysiu]Wine doesn't show up in the menus because it's a helper program, not a program that launches by itself.

For example, when I had FileZilla installed with Wine, my launcher for FileZilla was something like this: ```
wine "z:\home\username\.wine\drive_c\Program Files\FileZilla\FileZilla.exe"
``` Wine basically helps you launch a .exe file. Wine can't run by itself.[/QUOTE]

Thanks aysiu and all of you!

So, there should not be any wine icon in the menu.

A look in the wine user manual told me to type **winecfg** in the terminal. Then the wine configuration window opened up. The manual now will guide me.

:)

---

