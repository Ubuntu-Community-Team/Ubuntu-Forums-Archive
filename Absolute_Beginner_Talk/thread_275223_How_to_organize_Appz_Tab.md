---
title: "How to organize Appz Tab"
date: 2006-10-11
forum: Absolute Beginner Talk
---

### Post by bigben on 2006-10-11
Hi
When I go on aplications, I now have a Debian Tab which unfolds into many sub-tabs with all appz,games,shell,screen sub-tabs..
Its a bit annoying to have this, as it kinda gives me a double account of all appz I have installed. I'd like to "erase" the Debian tab and have all the things in the respective subfolders of the applications tab in the taskbar..
How can I do this?
TIA

---

### Post by Kateikyoushi on 2006-10-11
You can organize the menu in system >> preferences >> menu layout.

---

### Post by AndyCooll on 2006-10-11
Not sure if this is what you mean, however if you have added the Debian Menu under "Applications" you can remove it as follows:

```
sudo apt-get remove menu menu-xdg pdmenu
```

:cool:

---

### Post by CatKiller on 2006-10-11
Right-click on the Applications menu and select Edit Menus. Click on Applications. Those menu entries with a tick next to them are visible. Those without, aren't.

---

### Post by bigben on 2006-10-11
Its amazing how simple things are after you try them once...;)

Thanks a lot guys..

---

