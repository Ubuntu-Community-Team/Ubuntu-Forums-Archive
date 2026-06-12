---
title: "deleted menu item?"
date: 2007-04-07
forum: Absolute Beginner Talk
---

### Post by garyed on 2007-04-07
While going thru the "edit menu" I accidentally deleted the system tools.
Now it doesn't show up in the edit menu.
Anyone know how I can get it back?

---

### Post by LaurelLynn on 2007-04-07
Dear garyed,

Go back to Edit Menus. Each of the Appications has a check box next to it, some with a black square inside, some without.  You probably unchecked the box by accident. Just go back and check  it again so that there is a black square inside. The System Tools should come right back (or it did when I just un-checked and rechecked it on my system).

Laurel Lynn

---

### Post by garyed on 2007-04-07
> **LaurelLynn said:**
> Dear garyed,

Go back to Edit Menus. Each of the Appications has a check box next to it, some with a black square inside, some without.  You probably unchecked the box by accident. Just go back and check  it again so that there is a black square inside. The System Tools should come right back (or it did when I just un-checked and rechecked it on my system).

Laurel Lynn

Actually thats where I was when I deleted the system tools.
When I first checked the box & closed the edit menu it showed up under applications.
I went back into edit menus & tried to move it with the mouse & now its gone.
I can't find system tools anywhere now in the edit menu to put a check in it.

---

### Post by ardchoille42 on 2007-04-08
The gnome menu is parsed from items in /usr/share/applications, ~/.local/share/applications and a few other places. When you change the menus two files are written in ~/.config/menus. I have noticed that if I move those two files to another directory and do "killall gnome-panel" to restart the panel and reparse the menus, then the menus are reset back to the defaults. You might try moving those two files in ~/.config/menus, killall gnome-panel and see if the deleted items re-appear. If they do, you can tweak your menus again.

---

### Post by garyed on 2007-04-08
I think I found system tools  programs in that directory & somehow just the name got changed from "system tools" to "other".
Can anyone confirm what programs are in the "sytem tools"
The ones I found were :

Root Terminal
Floppy Formatter
GDebi Package Installer
Configuration Editor
Ubuntu Device Database

---

