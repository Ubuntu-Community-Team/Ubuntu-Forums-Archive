---
title: "New theme not in settings manager after unpacking..."
date: 2008-01-17
forum: Absolute Beginner Talk
---

### Post by ~Maxx on 2008-01-17
Hello.  I'm making my first attempt at installing a new theme to Xubuntu (Feisty).  I've downloaded and unpacked it, then copied it to the .themes folder in my Home directory.  If I understand correctly it should now be available under Settings > Settings Manager > User Interface.  Unfortunately this is not the case.  Anyone have an idea as to what I might have done wrong?

As always - thank you.

---

### Post by ~Maxx on 2008-01-17
Sorry to bump, but I've been messing with this and trying to find more info throughout the day and haven't had any luck whatsoever.  It seems that I've done everything correctly.  Ideas anyone?

Thank you

---

### Post by PeterJS on 2008-01-17
Sounds right. Where do you get the theme from?

---

### Post by ~Maxx on 2008-01-17
Found it at the xfce-look.org site.  [Here.]("http://www.xfce-look.org/content/show.php/Neutronium-Xfwm4?content=46566")

Thanks for the reply!

---

### Post by PeterJS on 2008-01-17
It's an XFWM4 theme, it would be selected under: Settings > Settings Manager > Window Manager.

If you were looking for a GTK widget theme you might try this one:
[http://www.xfce-look.org/content/show.php/Neutronium+Unity?content=59189](http://www.xfce-look.org/content/show.php/Neutronium+Unity?content=59189)

---

### Post by ~Maxx on 2008-01-17
Really!?!?  Huh!  Just a few questions now...

1) Would this file still need to be in my Home/.themes directory in order to show up in the windows manager?  Because it doesn't seem to be available when I look there either.

2) What's an XFWM4 theme?

3) what's a GTK widget theme?

I like the look of the theme you suggested!  I'm going to give it a try.  Wish me luck!

Thank you...

---

### Post by PeterJS on 2008-01-17
> **~Maxx said:**
> Really!?!?  Huh!  Just a few questions now...

1) Would this file still need to be in my Home/.themes directory in order to show up in the windows manager?  Because it doesn't seem to be available when I look there either.

Yeah I tried it out in in $HOME/.themes/. It ended up that I had a path that looked like:
$HOME/.Themes/Theme_Name/XFWM4/*a bunch of images*

> 
2) What's an XFWM4 theme?

XFWM4 is the default window manager for XFCE. So a theme for it would control title bars, close buttons, and borders. The are lots of window managers, each desktop environment pretty much has it's own. KDE as kwin and kwin-kde4, gnome has metacity, and compiz's emerald window manager will work on any desktop environment, provided you can run compiz.

> 
3) what's a GTK widget theme?

Application widgets (not to be confused with desktop widgets), are things like buttons, scroll bars, text boxes, tabs, all those common things you find in programs. Widget tool kits are a big collection compatible ways describing widgets and the themes they use. The two main widget kit's are gnome's GTK, and KDE's QT. Xfce also uses GTK for it's applications. So changing your widget theme would change the look of all those common UI elements for Gnome and Xfce applications.

---

