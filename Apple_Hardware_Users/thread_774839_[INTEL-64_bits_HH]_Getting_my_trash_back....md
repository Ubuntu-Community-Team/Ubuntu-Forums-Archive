---
title: "[INTEL-64 bits HH] Getting my trash back..."
date: 2008-04-29
forum: Apple Hardware Users
---

### Post by GeneralSunTzu on 2008-04-29
I agree it is a small detail, but still it would be nice...
To get back my trash can on the desktop, and not on the panel, I tried:

1. sudo gconftool;
2. once into gconftool, nautilus then desktop then icons;
3. made the icon for the trash can (and for other things) visible.

It neither works instantly nor after reboot.

What am I making wrong? 
Am using the 'mist' theme, but that should be irrelevant.

I took a deep swim into the gnome doc, not for the faint-hearted, and it seems that the only way to do it is this, though usage of gconftool is not recommended (for reasons which seem arcane).
Anybody can help, please?

---

### Post by benanzo on 2008-04-29
Don't use sudo as that will make the change for the root user only.

Easiest way is to hit "Alt-F2" then type "gconf-editor"

Go to Apps -> nautilus -> desktop

Then put a check in the box next to "trash_icon_visible"

Good Luck!

---

### Post by GeneralSunTzu on 2008-04-29
> **benanzo said:**
> Don't use sudo as that will make the change for the root user only.

<snip>

Good Luck!

That was it, Benanzo, thanks a billion! It worked perfectly!

---

### Post by cyberdork33 on 2008-04-29
> **benanzo said:**
> Don't use sudo as that will make the change for the root user only.

Easiest way is to hit "Alt-F2" then type "gconf-editor"

Go to Apps -> nautilus -> desktop

Then put a check in the box next to "trash_icon_visible"

Good Luck!
yep, this is one of the first things I do on a new install (in addition to adding a Computer Icon, and the Home folder.

---

