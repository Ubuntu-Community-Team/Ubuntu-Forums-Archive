---
title: "Which applications safely to be removed"
date: 2006-02-11
forum: Absolute Beginner Talk
---

### Post by mr_crimp on 2006-02-11
Hi, 
I have just installed a fresh new ubuntu 5.10 on my laptop but I just have a question about which applikations I safely can remove whitout to mess up other applikations and gnomes functionality. These applikations is the ones which I don't use and would like to remove:

- All the gnome games
- Evolution
- Xsane
- Gnomemeeting
- Totem
- Rhythmbox
- XMMS

What is the best way to remove these applikations? apt-get remove {packagename}?

Thanks for your help.

---

### Post by Kiwinote on 2006-02-11
You should be able to remove most of them, if not all of them using the synaptic package manager. If the changes affect another package it will come up with a screen asking you if you want the affected packages removed. As long as it only wants to remove ubuntu-desktop it's safe to remove them.

Kiwinote

---

### Post by mr_crimp on 2006-02-12
thanks...

---

### Post by kaamos on 2006-02-12
Removing Totem disables the video thumbnailing feature though.

---

