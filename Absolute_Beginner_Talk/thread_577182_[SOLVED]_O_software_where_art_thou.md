---
title: "[SOLVED] O software where art thou?"
date: 2007-10-15
forum: Absolute Beginner Talk
---

### Post by Niniel on 2007-10-15
Uhm, where does Ubuntu put apps that are installed via the Add tool? I got myself LGeneral, and now want to/need to install campaigns and scenarios. Can't find the directory though. :)

---

### Post by oodledoodle on 2007-10-15
try /usr/lib64 or /usr/lib32

---

### Post by RomeReactor on 2007-10-15
Hi. In Synaptic, search for the game, once it shows up highlight it and press the "Properties" button (or right-click the package and select "Properties"); then go to the "Installed Files" tab, and there you can see where everything is located.

---

### Post by Niniel on 2007-10-15
Ok, that worked, thank you.
Unfortunately, I don't ssem to have write permission. :(

---

### Post by RomeReactor on 2007-10-16
You can open Nautilus with root privileges from the terminal (or by pressing ALT+F2):
```
gksudo nautilus
```
Just remember to be **very** careful with what you do while nautilus is open this way, and as soon as you're done copying files, close Nautilus.

---

### Post by Niniel on 2007-10-16
Ok, thanks.

---

