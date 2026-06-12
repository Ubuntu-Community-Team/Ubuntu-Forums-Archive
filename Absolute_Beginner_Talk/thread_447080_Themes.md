---
title: "Themes"
date: 2007-05-17
forum: Absolute Beginner Talk
---

### Post by Jdratcliffe on 2007-05-17
hi guys this may sound really crap question to ask but i just downloaded kl new theme [http://www.gnome-look.org/content/show.php/Ubuntu+Basic+Black?content=58111](http://www.gnome-look.org/content/show.php/Ubuntu+Basic+Black?content=58111)

but i never seen a tar.gz file b4 (on ubuntu now) r they lynux version of zip ? if so what do i need to open / install my theme?

---

### Post by aysiu on 2007-05-17
That's a login screen theme.

.tar.gz is, in fact, a zipped file, but **do not unzip this file**

To install it, go to System > Administration > Login Window and then click **Install Theme**

Find the .tar.gz file and select it.

Then, to use it, make sure the circle next to the theme is filled in (black).

---

### Post by Jdratcliffe on 2007-05-17
ok so if these are login in themes how do i change a theme set eg icons and "start" bar (top bar / line of buttons?

---

### Post by aysiu on 2007-05-17
Well, when you go to [http://www.gnome-look.org](http://www.gnome-look.org), you'll see a bunch of types of themes on the left side.

GDM themes, as you've discovered, are login screen themes.

GTK themes control the window border and Metacity themes control the window controls (I may have those two mixed up--it may be Metacity that does the window border and GTK the internals).

Icon themes control icons.

To install GTK, Metacity, or icon themes, go to System > Preferences > Themes and drag and drop the .tar.gz file into the Theme Manager Window.

You don't need themes for the top bar, though--you can right-click the bar and adjust the properties yourself (transparency, size, etc.).

---

### Post by Jdratcliffe on 2007-05-17
oh and one more thing sorry for being a pain how do i unistall a theme?

---

### Post by Jdratcliffe on 2007-05-17
thanxs

---

### Post by aysiu on 2007-05-17
> **Jdratcliffe said:**
> oh and one more thing sorry for being a pain how do i unistall a theme?
I think the theme manager window and the login screen setup allow you to remove themes by clicking the minus sign.

If not, you can manually remove them. The themes you install through the theme manager window will live in either ~/.themes (also known as /home/jdratcliffe/.themes) or ~/.icons

All the files and folders beginning with **.** are hidden by default, so press Control-H to see them.

The login screen themes live in /usr/share/gdm/themes, which is a system folder, so you'll have to launch a browser with administrative (or root) privileges--some tips on that here:
[http://www.psychocats.net/ubuntu/permissions#gui](http://www.psychocats.net/ubuntu/permissions#gui)

---

### Post by Jdratcliffe on 2007-05-17
kl thxs for your help ill have fun p[laying 2morrow i 2200 now need some sleep have work ...:<

---

