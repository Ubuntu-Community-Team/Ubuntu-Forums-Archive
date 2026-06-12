---
title: "Remove KDE from Kubuntu install?"
date: 2006-09-18
forum: Absolute Beginner Talk
---

### Post by Irish J on 2006-09-18
Hey all, I was wondering if it was possible to remove KDE as my windows manager in Kubuntu?

I have KDE, Gnome and XFCE (the latter two i installed using apt-get install xubuntu-desktop and apt-get install ubuntu-desktop to get the metapackages)

Right now i'd like to use just XFCE, is there any way to remove KDE?

---

### Post by Metacarpal on 2006-09-18
[Here's a page]("http://www.psychocats.net/ubuntu/purexfce") with instructions for removing Kubuntu (KDE) and/or Ubuntu (Gnome) to leave you with just the xfce system.  The commands need to be copied and pasted into Terminal (Applications menu > Accessories > Terminal).

The first section is to remove Gnome, and the second is to remove KDE.

---

### Post by Irish J on 2006-09-18
Thanks gent, will give it a try now.

---

### Post by Irish J on 2006-09-18
This worked perfectly for me, but i also had to do

```
sudo apt-get install xubuntu-desktop
``` to get XFCE working properly after removing the other two.  no idea why (shared libraries maybe?)

---

