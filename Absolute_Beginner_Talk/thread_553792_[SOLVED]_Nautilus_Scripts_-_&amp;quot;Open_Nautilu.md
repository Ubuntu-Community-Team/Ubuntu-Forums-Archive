---
title: "[SOLVED] Nautilus Scripts - &amp;quot;Open Nautilus, &amp;amp; any file with gedit with a right click,"
date: 2007-09-18
forum: Absolute Beginner Talk
---

### Post by MozartlovesUbun2 on 2007-09-18
Nautilus Scripts - "Open Nautilus, & any file with gedit with a right click, as root" (GNOME ONLY)

On a newly installed Feisty PC, I'm trying to avoid "Automatix" but automatix comes with this handy feature, with it I can

#Open any file with gedit editor as root
#Open the current location in Nautilus as root
#Open the gnome-search-tool in current location

If you have used Automatix you may know this,

So how do I get these features with installing Automatix?

thanks

---

### Post by Kilz on 2007-09-18
Open a terminal and type

```
gksudo nautilus
```

---

### Post by ThrobbingBrain66 on 2007-09-18
Installing the nautilus-gksu package adds an "Open as adminstrator" (using gedit) option to the right-click menu.

---

### Post by MozartlovesUbun2 on 2007-09-18
> **Kilz said:**
> Open a terminal and type

```
gksudo nautilus
```

This is for my uncles machine, needs to be super windows style easy, too early to teach him command line stuff (hehe, not that I'm any fluent in the Terminal)

I'll stick to the "nautilus-gksu"

thanks

---

### Post by justleen on 2007-09-18
create a script in .gnome2/nautilus/scripts/open_as_root

containing:
#/bin/bash
gksudo gedit $1


for root nautilus:
(create a new script...)
#!/bin/bash
gksudo nautilius

---

