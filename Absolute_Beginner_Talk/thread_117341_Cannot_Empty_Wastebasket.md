---
title: "Cannot Empty Wastebasket?"
date: 2006-01-14
forum: Absolute Beginner Talk
---

### Post by _simon_ on 2006-01-14
I deleted a directory (wine) but it won't let me empty it from the wastebasket.

It says:

Error While Deleting

"/home/simon...wine.dirs" cannot be deleted because
you do not have permissions to modify its parent folder"


So how do I get rid of it?

---

### Post by Zelut on 2006-01-14
Occasionally it becomes needed to manually dump the trash.  If you need this try the following from the terminal:

[B]cd ~/.Trash
sudo rm -R  *[/B]

---

### Post by _simon_ on 2006-01-14
Thanks - I tried that but it's still there?

---

### Post by aysiu on 2006-01-14
How about you Alt-F2 and type ```
gksudo nautilus
``` and then navigate to the /home/simon/.Trash folder and try to delete it graphically.

You may have to go to Preferences and enable the *delete* (as opposed to *move to trash*) command.

---

