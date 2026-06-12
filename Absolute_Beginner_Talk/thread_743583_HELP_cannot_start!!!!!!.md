---
title: "HELP cannot start!!!!!!"
date: 2008-04-02
forum: Absolute Beginner Talk
---

### Post by Mauler5858 on 2008-04-02
I accidentally deleted quite a few packages including GDM, most of gnome, when trying to remove alsa.  How can i reinstall these back to defaults off of the live cd?

---

### Post by meborc on 2008-04-02
you need to reinstall a package called "ubuntu-desktop"

boot to rescue mode... insert cd and type

> sudo apt-get remove ubuntu-desktop
sudo apt-get install ubuntu-desktop

EDIT: be sure you have your cd in a sources.list file
ubuntu-desktop is just a metapackage... it tells the system to install everything a standard ubuntu desktop needs

---

