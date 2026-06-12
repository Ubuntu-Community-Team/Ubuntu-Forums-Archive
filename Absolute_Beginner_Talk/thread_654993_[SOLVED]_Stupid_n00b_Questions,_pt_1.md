---
title: "[SOLVED] Stupid n00b Questions, pt 1"
date: 2007-12-31
forum: Absolute Beginner Talk
---

### Post by ZOOstation on 2007-12-31
I've been piling up stupid questions I'm too embarrassed to ask. Here's the first one I'm feeling brave enough and humble enough to post about.

In one of my many attempts to get my wlan running reliably, I seem to have created a folder that I don't have permission to change. I created it and its contents, so why can't I delete it? It's not being used for anything. Is there any way to double-check that?

The exact message is: "Cannot move "/home/joey/wifi/80211g" to the trash because you do not have permissions to change it or its parent folder." It's not the parent folder, this one has the little lock image on its icon and I can successfully move the parent folder "wifi" to the trash, but not delete it once it's there because of its unchangeable contents.

Is there any way to delete this, or do I simply have to ignore it like a giant squid in my kitchen?

---

### Post by taurus on 2007-12-31
You can remove that directory from a terminal or you can use nautilus with root privilege.

Applications -> Accessories -> Terminal
```
gksudo nautilus
```

---

### Post by Majorix on 2007-12-31
Try
```
sudo rm -rf /home/joey/wifi/80211g
```
Warning: This will most likely successfully delete all of that folder and its contents!

Why I offer this solution: I believe the folder is somehow owned by root.

---

