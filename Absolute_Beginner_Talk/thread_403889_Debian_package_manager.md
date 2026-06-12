---
title: "Debian package manager"
date: 2007-04-07
forum: Absolute Beginner Talk
---

### Post by delilahjed44 on 2007-04-07
[COLOR="DarkRed"]Ok Hey, I must have downloaded the Debian Package manager of some sorts but I am not for sure.  I am a newbie.  Using Ununtu 6.10.  Suddenly in my APPLICATIONS as I scroll down it sais Debian>apps-games-help-Xshell.  Well the list goes on and added to it is medias and programs I alread have by default in Ubuntu, so I dont even need this, and want to rid it.  I went through add-remove, it said CANNOT REMOVE GDEBI one or more applications depend on it remove it through synpatic.  Well sind it is listed in system tools in add and remove I am wondering if I should remove it.  Heres the deal, it was not there before, I dont need double programs and anothe menu of a system in itself operating out of my applications.  I cant seem to find what it is and surle someone has the same thing, but in their case it may benefit them.  I need to un-install it.  Thanks

Sherri[/COLOR]

---

### Post by yabbadabbadont on 2007-04-07
Just run the menu editor, Alacarte, and uncheck the Debian submenu.  Alacarte should be under Applications->Accessories.  You may need to log out and back in so that the panel reloads in order for it to take affect.

---

### Post by solar george on 2007-04-07
The debian packaging system or apt is used by ubuntu as its packaging system, Ubuntu is in fact based on Debian. As for the menu you can use the alacarte menu editor (should be under preferences) to stop the Debian menus showing.

---

### Post by delilahjed44 on 2007-04-07
[COLOR="DarkRed"]Hey Thanks, well since it was never there before and suddenly after after having Ubuntu for a time, I am wondering how it got there, so its an original package? the programs are not doubled up? because I never put this in the menu? this is why I am wondering, I dont want space chewed up from double packages, so I wanted to eliminate that. 

Sherri[/COLOR]

---

### Post by heimo on 2007-04-07
Alternative way to get to alacarte (menu editor) is right-clicking on "Applications" (or the Ubuntu logo on your screens top left corner) and selecting "Edit menus". Then uncheck anything you don't want to show up in menus.

---

### Post by solar george on 2007-04-07
You are simply seeing the debian menu, can't think how it suddenly appeared, but the way that the package manager works prevents doulble installing you packages.

---

### Post by yabbadabbadont on 2007-04-07
The programs aren't installed more than once.  It is just that something caused the Debian standard menu structure to show up in your menu.  It may be that the "menu" or "menu-xdg" programs got installed as a dependency of something else you installed, and that caused it to show up all of a sudden.

---

