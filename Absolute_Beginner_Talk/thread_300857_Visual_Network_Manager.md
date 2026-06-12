---
title: "Visual Network Manager"
date: 2006-11-16
forum: Absolute Beginner Talk
---

### Post by pteri498 on 2006-11-16
Hi. I'm using a KDE desktop manager. In Gnome, as is default on Ubuntu, the network manager provided shows visually upstream and downstream from the tray icon. (One light for downloads and one for uploads)

This is important for me as my internet connection is not great and I'd like to know exactly when the internet stops moving for me. However, I can't find a network manager that will give me this information on the tray icon, like the one that Gnome or Windows XP provides.

Does anyone know of a network manager that can do this for KDE?

---

### Post by BarfBag on 2006-11-16
I'm pretty sure you can install the GNOME network manager in KDE through apt-get.  Do you know the exact name of it?  If not, try this:

1.  Open up Terminal, and type:

> sudo apt-cache search gnome

2.  Look through the list it brings up until you find the name.

3.  Then type:

> sudo apt-get install <name>

Hope this helps.  Again, I'm not 100% sure this will work.  Worth a try, though.

---

### Post by pteri498 on 2006-11-16
Well that's the thing though. The network manager I'm talking about in gnome appears to not be a program with a tray icon, but more a program that runs completely within the taskbar. Think it's called an applet or something along those lines.

Just trying to find a similar program, since KDE doesn't appear to have such an applet.

---

### Post by Marsolin on 2006-11-16
KDE doesn't come with it, but BarfBag's point was that you can install gnome-netstatus-applet and probably still use it in KDE.

---

