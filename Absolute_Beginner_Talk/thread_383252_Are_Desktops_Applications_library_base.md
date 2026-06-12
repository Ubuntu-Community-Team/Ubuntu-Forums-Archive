---
title: "Are Desktops Applications library base"
date: 2007-03-13
forum: Absolute Beginner Talk
---

### Post by Lowva on 2007-03-13
New in the linux world, and i am interested in knowing if programmed GUI applications are base on the Desktop GUI Enviroment, or can they be compile to run on any desktop, as long as you are running the Library need it. and are there any Gui Applications like Maya 3d etc that will only work and have been made so to work on a specific Desktop

Thank you very much

---

### Post by 23meg on 2007-03-13
Mostly, applications depend on libraries that make up GTK and QT, the widget toolkits used by GNOME and KDE respectively. But you can use a GTK app in KDE, provided that you have the required GTK libraries, and vice versa. When you install a GNOME app with APT in your KDE environment, the required GTK library dependencies will automatically be installed. 

Some applications also require some desktop environment features other than the widget toolkit; in that case, those will be installed as well, and you can use pretty much every app in every environment. But since you'll be loading extra libraries, mixing and matching apps and environments is generally more resource intensive.

Does Maya require a certain environment? I wasn't aware that it did.

---

