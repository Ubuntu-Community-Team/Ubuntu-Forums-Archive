---
title: "problems starting programs with login"
date: 2007-03-28
forum: Absolute Beginner Talk
---

### Post by unabatedshagie on 2007-03-28
I've just done a reinstall of Ubuntu and am having a small problem which I can't figure out how to solve.

Anything that I add to **System > Preferences > Sessions > Startup Programs** doesn't say in the list.

For instance I add beryl-manager to it, close it and if I open it again the entry's gone.

Does anyone know how I can fix this or if there is another way to make programs start at login.

---

### Post by eljalill on 2007-03-28
You might have a problem with permissions... But I am not sure why that would occur!
You can add startup programs manually through making a .desktop script and save it in ~.config/autostart (in your home directory). Just copy an existing .desktop and change the "exec" line.

Lok for exisitng .desktops through locate for example.
(locate .desktop)

---

### Post by ComplexNumber on 2007-03-28
installing 'gnome-session' may be the answer. just do:
**sudo apt-get install gnome-session**

---

### Post by unabatedshagie on 2007-03-28
> **ComplexNumber said:**
> installing 'gnome-session' may be the answer. just do:
**sudo apt-get install gnome-session**Tried it but it says there are no packages to install.

> You might have a problem with permissions... But I am not sure why that would occur!
You can add startup programs manually through making a .desktop script and save it in ~.config/autostart (in your home directory). Just copy an existing .desktop and change the "exec" line.

Lok for exisitng .desktops through locate for example.
(locate .desktop)Will give this a try, thanks

---

