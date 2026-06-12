---
title: "Program installed with wine won't remove"
date: 2007-07-27
forum: Absolute Beginner Talk
---

### Post by Specter043 on 2007-07-27
I installed winamp with wine and wine-doors for my girlfriend before finding xmms.  I then deleted wine and Wine doors, as well as their folders, but for some reason winamp still shows up under my sound and video apps.  If it was deleted, why should it still be there?

---

### Post by Majorix on 2007-07-27
Why didn't you uninstall it using the
```
uninstaller
```

Its a program that uninstalls programs installed with wine.

Also did you remove ~/.wine folder? Its hidden by default. You have to go to your home folder and do a ctrl+h to show it. Then delete it.

If that doesn't work, reinstall wine and use uninstaller.

---

### Post by Specter043 on 2007-07-27
it seems like just the option for winamp is there, because now that I reinstalled wine, it doesn't show up when I run it, or in the uninstaller.  Does anyone know how to just remove it from the applications menu then?

---

### Post by st33med on 2007-07-27
Try this: System Tools >> Wine Software Uninstaller

Haven't tried it. It is in the newer versions.

---

### Post by Specter043 on 2007-07-27
It doesn't show up in that menu :(

---

### Post by dpar on 2007-07-27
Do you mean the Ubuntu Applications menu?
Right click the panel bar, click Edit Menu, Click Sound & Video on the left side, find the winamp entry and right click, click delete.
Clickety click......lol, hope that works.

---

### Post by Majorix on 2007-07-27
```
sudo alacarte
```

Then remove the entry in the menu and it will be gone.

---

### Post by dpar on 2007-07-27
> 
Code:

sudo alacarte

Then remove the entry in the menu and it will be gone.

Or that.....lol

---

### Post by Specter043 on 2007-07-27
Thanks for the help, That solved the problem.

---

