---
title: "Removing Wine app links?"
date: 2006-09-30
forum: Absolute Beginner Talk
---

### Post by WalmartSniperLX on 2006-09-30
I uninstalled several wine programs (by removing the files from the .wine Program Files folder). But, I still have the menu entries in the menu. I dont want to just delete the entries via the menu editor because I want to know what is making them appear there. How do I delete them?

---

### Post by CatKiller on 2006-09-30
I think that Wine interprets the install scripts and puts .desktop entries in ~/.gnome/apps/Wine. You could delete these files if you want them to go away.

EDIT: Just noticed you're using Kubuntu. So they'll probably be somewhere else instead ;)

---

