---
title: "menu missing almost everything !!!"
date: 2006-11-11
forum: Absolute Beginner Talk
---

### Post by evilsee on 2006-11-11
Hi,

Im running ubuntu edgy,

When I select the menu all I see is "places", "system" and the quit button.

I am pretty certain but not entirely sure that this happened after I installed the SLED menu applet from novel.

How do I go about getting the default sub menu's back for my box or is there some other way I can fix this.

Thanks

---

### Post by Albi on 2006-11-11
Try re-adding it


Right click on the menu and click "remove"

Then right click, add to panel, and click menu bar or main menu

---

### Post by Albi on 2006-11-11
Or maybe they're not checked, so go to system-->preferences--->menu layout

---

### Post by evilsee on 2006-11-11
Ive tried removing and adding the menu, no luck.

I tried right clicking and editing the menu, it appears to load, but no application appears and when I got system->preferences->menu-layout the same thing happens, it appears to start loading, but nothing, no application loads.

Ive also tried alacarte, but it just gives me a whole bunch of errors.

Ive also had alook at the /usr/share/desktop-directories and all the .directory files appear to be there.

as well as the  /etc/xgd/menus dir has the applications.menu and a couple other .menu files.

It almost seems like there could be a setting or config file thats hiding the other submenus.

Im really stuck, ubuntu rocks except when things go wrong.

---

### Post by evilsee on 2006-11-11
ok I solved it theres a directory called /home/username/.config
it has a menus directory and in this directory are .menu files, I rename the .config and restarted gdm and voila I had a menu.

as I test I removed a program from the menu and the .config directory was recreates so it definitely  a user specific menu settings

---

### Post by uric on 2007-06-20
you saved me alot of trouble. Renaming the .config folder fixed it for me as well!

Thanks!

---

