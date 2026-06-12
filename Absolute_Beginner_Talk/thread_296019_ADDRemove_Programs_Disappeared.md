---
title: "ADD/Remove Programs Disappeared ?"
date: 2006-11-09
forum: Absolute Beginner Talk
---

### Post by livinginx on 2006-11-09
I still use Gnome, but I lost my Applications / Add Remove Programs button.

I reinstalled right after I noticed it, but can't figure out for the life of me how or why.  I use synaptic, so it isn't a big deal, just trying to figure it out.

---

### Post by linuxhacker on 2006-11-09
Go > System > Preferences > Menu Layout and check to see if the Add/Remove is selected. This is in Edgy. In Dapper go > Applications > Accessories > Alcarte I believe. I hope this is helpful.

---

### Post by aysiu on 2006-11-09
Try pasting these command in the terminal: ```
sudo aptitude update
sudo aptitude install gnome-app-install
gksudo gnome-app-install
``` If that launches Add/Remove Programs, all you need to do is add it to the menu by using A la Carte, as linuxhacker suggested.

---

### Post by livinginx on 2006-11-09
aysiu, thank you as usual :-D

---

