---
title: "Lost and Found:  KControl modules showing up in Lost and Found menu only"
date: 2007-04-03
forum: Absolute Beginner Talk
---

### Post by DizzyTech on 2007-04-03
All of the modules that should be in Kcontrol (or Kubuntu's System Settings equivalent, I prefer KControl) are showing up in the Lost and Found KMenu category, but not Kcontrol.

I've also noticed some old icons in there, so I think it must be from my incomplete Kubuntu installation a long time ago (AmaroK + dependencies + build dependencies).

I've already completely purged Kubuntu-Desktop and its contents, and removed my .kde folder.  Is there any way to get rid of my KMenu configuration and let it rebuild?  Any ideas?

---

### Post by mahy on 2007-04-03
wouldn't it be easier just to edit the menu?? it's easy, just right-click the item you wish to edit and select "edit" or some such.

---

### Post by DizzyTech on 2007-04-03
No, no, no... I need to get all of these items (in excess of fifty) back as they were as Kcontrol modules.  That's the only problem I have, it'd just be easier to restore them.

Know that I can't change any of the settings until this is fixed.

---

### Post by loyeyoung on 2008-02-09
In a terminal or console:
```
# sudo ln /etc/xdg/menus/kde-applications-merged/kde-essential.menu /etc/xdg/menus/applications-merged/
```
Happy Trails,

Loye Young
Isaac & Young Computer Company
Laredo, Texas
[http://www.iycc.net](http://www.iycc.net)

---

