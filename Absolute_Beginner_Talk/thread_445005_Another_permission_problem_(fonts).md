---
title: "Another permission problem (fonts)"
date: 2007-05-15
forum: Absolute Beginner Talk
---

### Post by tarchy on 2007-05-15
Whilst trying to paste  a new font into usr/share/wine/fonts it says I don't have permission! I am the root admin, ofcourse....anybody know the cause/solution?

---

### Post by tarchy on 2007-05-15
So it says I am NOT the root admin! GRRR!!!!

[img]http://img357.imageshack.us/img357/7483/screenshotpa4.png[/img]

(Look at the bottom of the window)

---

### Post by LaRoza on 2007-05-15
Are you sure you are root? Unlike Windows, there is usually no administrative account. Try moving the file, assuming that that is what is supposed to happen, as root.

sudo mv /home/tarchy/Tahoma.tff /usr/share/wine/fonts


-edit change the owner, see this page for details, [http://webtools.live2support.com/linux/chown.php](http://webtools.live2support.com/linux/chown.php)

---

### Post by netwerx on 2007-05-15
> **tarchy said:**
> Whilst trying to paste  a new font into usr/share/wine/fonts it says I don't have permission! I am the root admin, ofcourse....anybody know the cause/solution?

Are you trying to install a font for wine use, or for ubuntu use?

to open up a root session in Nautilus, run in terminal:

"gksudo nautilus"

you should now have root access to everything.

---

### Post by sessine on 2007-05-15
Actually, you normally do not have admin rights BUT, you are a member of the superuser group which allows you to use the 'sudo' command in a terminal  (SuperUserDO) to execute specific commands with root privileges.

Try opening a terminal and cd into the directory which currently contains the font and do

sudo cp *font* /usr/share/wine/fonts

(where *font* is the filename of the font you need

---

