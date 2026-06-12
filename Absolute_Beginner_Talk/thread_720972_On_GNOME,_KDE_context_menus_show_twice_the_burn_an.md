---
title: "On GNOME, KDE context menus show twice the burn animation!"
date: 2008-03-10
forum: Absolute Beginner Talk
---

### Post by Fixman on 2008-03-10
This is really disturbing when wanting to use the Amarok context menu!

---

### Post by Arkenzor on 2008-03-11
Since it's not very clear, I'll assume that you're using compiz-fusion, and that you already installed ccsm and know how tu launch it (since burn is not one of the default animations - I think). 
(If not, check the last paragraph)

Now, the thing is that Qt (KDE) applications don't identify themselves correctly by default (correctly to compiz, I don't know about standard compliance), and compiz can't identify menus as menus, tooltips as tooltips, etc.
The solution is easy, enable the Workarounds plugin. Also check its configuration and make sure "Qt Window Fix" is enabled. This should allow compiz to identify Qt widgets properly.


If you haven't installed ccsm (in which case I don't know how you ended up with the Burn effect, but well...), you can get it with Synaptic. The package is called compizconfig-settings-manager.
Then, run the "ccsm" command or go under System->Settings->Advanced Desktop and Effects Settings (I think) to open a configuration tool for compiz-fusion.
(I think you can also run ccsm from the "Custom Effects" option in your Gnome configuration, but I don't remember clearly since I don't use Gnome)

---

### Post by Fixman on 2008-03-11
> **Arkenzor said:**
> Since it's not very clear, I'll assume that you're using compiz-fusion, and that you already installed ccsm and know how tu launch it (since burn is not one of the default animations - I think). 
(If not, check the last paragraph)

Now, the thing is that Qt (KDE) applications don't identify themselves correctly by default (correctly to compiz, I don't know about standard compliance), and compiz can't identify menus as menus, tooltips as tooltips, etc.
The solution is easy, enable the Workarounds plugin. Also check its configuration and make sure "Qt Window Fix" is enabled. This should allow compiz to identify Qt widgets properly.


If you haven't installed ccsm (in which case I don't know how you ended up with the Burn effect, but well...), you can get it with Synaptic. The package is called compizconfig-settings-manager.
Then, run the "ccsm" command or go under System->Settings->Advanced Desktop and Effects Settings (I think) to open a configuration tool for compiz-fusion.
(I think you can also run ccsm from the "Custom Effects" option in your Gnome configuration, but I don't remember clearly since I don't use Gnome)

All you say is correct - Im sorry i didn't give more information. However, Qt workarounds is already enabled, and disabling it doesn't work either.

---

### Post by Fixman on 2008-04-04
Any more help?

---

