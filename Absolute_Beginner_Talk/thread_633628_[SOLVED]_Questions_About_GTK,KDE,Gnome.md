---
title: "[SOLVED] Questions About GTK,KDE,Gnome"
date: 2007-12-06
forum: Absolute Beginner Talk
---

### Post by cerealtx on 2007-12-06
could someone explain what these are, if they can be used together and if one is better than t he other? Are they like Desktop Managers?

---

### Post by spiderbatdad on 2007-12-06
google and wikipedia give awesome definitions.

---

### Post by PeterJS on 2007-12-06
> **cerealtx said:**
> could someone explain what these are, if they can be used together and if one is better than t he other? Are they like Desktop Managers?


KDE and Gnome are the two main desktop environments used to create a linux desktop. There are other desktops environments, like XFCE, but KDE and gnome are the oldest and most used. Gnome is designed around the idea of being easy to use and making it very obvious how to do what you want it to do. KDE is built around the idea that user want and should be able to control every aspect of their desktop with exacting control.

Underneath each desktop is the widget tool kit it uses to provide a consistent look and feel. What  the tool kit does is provide a standard way for programs to create their interfaces, so instead of each program having to deal with how to draw buttons, text boxes, and other things, they just tell their tool kit what kind of interface element they want, like say a button, and it does all the heavy lifting for them. This is nice because it makes programming easier, and because each program isn't directly controlling how it looks, just where the elements are, the tool kit also controls theming by determining how to draw the elements. The two big tool kits are GTK and QT. GTK is the tool kit used by the Gnome and XFCE desktop, and QT is used by the KDE desktop.

As to which is better, asking which widget tool kit is a silly question unless you plan on programming your own applications, each program will use the tool kit it was built with and there's not much you can do about that.

The question of which desktop environment is better is really a matter of personal preference and what you're expecting the desktop to do for you, try each out, keep the one you like.

You can definitely have as many desktops and toolkits installed as you like. The applications from any desktop environment will work in any other environment, but they won't necessarily look the same and some things like drag and drop won't work.

---

### Post by cerealtx on 2007-12-06
thank you so much for that excellent explanation it helped very much thank you for taking the time to help me! Your why this community is so great! peopel willing to help idiots like me ;)

---

