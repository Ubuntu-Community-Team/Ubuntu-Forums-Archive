---
title: "KDE trash in Gnome"
date: 2006-12-03
forum: Absolute Beginner Talk
---

### Post by taddy_porter on 2006-12-03
I use Konqueror and other KDE apps inside Gnome. The problem is they send to KDE's trash instead of Gnome's. 

How do I clear out the KDE trash from within Gnome?

I tried creating a script I put on the panel 

```
sudo rm -rf /home/<user>/local/share/Trash
```

It doesn't seem to work though.

---

### Post by stimpack on 2006-12-03
you missed a dot before local

```
rm -rf /home/<user>/.local/share/Trash
```

sudo rm -rf is one typo from a dead system.

---

### Post by taddy_porter on 2006-12-03
Sorry. Typo on the web, not my script. Still doesn't work though.

---

### Post by taddy_porter on 2006-12-07
Any help out there?

---

