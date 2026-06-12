---
title: "[SOLVED] &amp;quot;Edit as root&amp;quot; in gnome?"
date: 2006-07-11
forum: Absolute Beginner Talk
---

### Post by skrållarn on 2006-07-11
I want to know if there is a way to fast and easily edit a textfile i gnome.
as in KDE where you right click and choose "edit as root".?
I know I can use alt+F2 and type "gksudo gedit /etc/blablabla..." 

or is there a option/flag/setting/ to always start gedit with root permissions?

---

### Post by maskd on 2006-07-11
You can do this by using nautilus scripts.

To add a script, go to ~/.gnome2/nautilus-scripts, create a file, I called mine gedit-as-root, make this file executable by right clicking on it and selecting properties, selecting the permissions tab and checking the executable box. Open this file in gedit and insert the following:

```

#!/bin/sh
gksudo gedit $NAUTILUS_SCRIPT_SELECTED_URIS

```

Make sure that it is executable, now when you right click on a file, there will be a Scripts menu that you can go in and select, then choose gedit-as-root and it will attempt to open gedit as root on the files you have selected.

---

### Post by 23meg on 2006-07-11
Take a look at [this]("http://www.ubuntuforums.org/showthread.php?t=24008").

---

### Post by skrållarn on 2006-07-11
the nautilus script was just what I was looking for. thanx alot!

---

### Post by Gustav on 2006-07-11
Use gnome-open insted of gedit in the script, then you can open any file (not just text files) as root.

You can even open a directory with it to get permissions when using nautilus.

---

### Post by skrållarn on 2006-07-11
> **Gustav said:**
> Use gnome-open insted of gedit in the script, then you can open any file (not just text files) as root.

You can even open a directory with it to get permissions when using nautilus.

great!
thank you!

---

