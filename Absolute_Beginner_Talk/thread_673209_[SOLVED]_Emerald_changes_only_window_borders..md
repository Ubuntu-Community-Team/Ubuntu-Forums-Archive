---
title: "[SOLVED] Emerald changes only window borders."
date: 2008-01-20
forum: Absolute Beginner Talk
---

### Post by rhc on 2008-01-20
I download themes for emerald and use pre-loaded emerald themes.
It shows really nice windows but when i load them in emerald theme manager,only window borders change.
How can i change and where can i find themes that change not only borders also colors of menubar line and toolbars.

---

### Post by PurposeOfReason on 2008-01-20
Emerald only changes window boarders. Panels, scrollbars, etc. are all GTK themes. Find them at gnome-look.org.

---

### Post by rhc on 2008-01-20
If so,should i uninstall or close emerald to use full gtk themes?
What is their relation with compiz?

---

### Post by PurposeOfReason on 2008-01-20
GTK has no relation to compiz or emerald. I would use emerald and gtk at the same time. Just make sure that you find a GTK theme that goes well with your emerald theme. ;)

---

### Post by mcduck on 2008-01-20
> **rhc said:**
> If so,should i uninstall or close emerald to use full gtk themes?
What is their relation with compiz?

None.

Compiz is a window manager, responsible for window borders. GTK is the toolkit used to create graphical interfaces for programs, so it's responsible of how your applications look like.

GTK themes will not change your window borders, and window manager themes will not change your applications.

---

### Post by rhc on 2008-01-20
Is there a menu or manager that easily changes the themes of Gtk?
In preferences or somewhere?
After i installed a theme how can i load it or when i want to go back to original settings,will it be easy?

---

### Post by PurposeOfReason on 2008-01-20
Right click the desktop, choose changed background. Go to the themes tab and choose install.

---

### Post by rosegarden78 on 2008-01-20
Manually-installed Beryl + Compiz together is a recipe for disaster.  Eye candy is included by default in Gutsy 7.10+ release.  Your headache will get so bad looking at eye candy you'll want to use XFCE with Nautilus for the simplicity, power and speed.

Try typing in a terminal:

sudo aptitude remove beryl
sudo aptitude remove compiz
sudo aptitude purge beryl
sudo aptitude purge compiz

Then go to your regular Control Panel - Settings - Display Manager or right click the desktop.  Select a default theme like Human or Plastik.  Finally, where is says Window Decoration tab, turn off all effects or select none.

Or try adding KDM + XFCE from the repositories and run Xubuntu + Nautilus.

You may prefer speed, power and simplicity to eye candy.

---

### Post by rosegarden78 on 2008-01-23
Try this instead:
[http://ubuntuforums.org/showthread.php?t=385981](http://ubuntuforums.org/showthread.php?t=385981)

---

### Post by rosegarden78 on 2008-01-23
Try this instead:
[http://ubuntuforums.org/showthread.php?t=677959](http://ubuntuforums.org/showthread.php?t=677959)
I got it working on Xubuntu with Intel 915 graphics.

EDIT: Updated URL

---

### Post by rhc on 2008-01-23
Thanks resogarden.

---

### Post by rosegarden78 on 2008-01-26
You're welcome I also update the link on my last post if you want to use Xfce.

---

