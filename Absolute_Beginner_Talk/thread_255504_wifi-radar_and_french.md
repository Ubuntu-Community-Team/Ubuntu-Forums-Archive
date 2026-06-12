---
title: "wifi-radar and french"
date: 2006-09-11
forum: Absolute Beginner Talk
---

### Post by GNUtoo on 2006-09-11
hello i have 2 computer under ubuntu
one is in english and the one for my family is in french
the problem is that the english can install wifi-radar but the french one can't:
# apt-get install wifi-radar
Lecture des listes de paquets... Fait
Construction de l'arbre des dépendances... Fait
E: Impossible de trouver le paquet wifi-radar

it says that it can't find the wifi-radar packadge

what should i do? is there a .deb somewhere for wifi-radar?

---

### Post by Metacarpal on 2006-09-11
It may be that the mirror you're using for downloads doesn't have wifi-radar for some reason.  Another though: have you enabled extra repositories on the French-language computer?  Wifi-radar is in the Universe repo, so you'll need to enable that to install it.

Or, worse comes to worst, you can download it [from here]("http://archive.ubuntu.com/ubuntu/pool/universe/w/wifi-radar/").  (Just linked the folder, not the deb - don't know your computer architecture, don't want to make faulty assumptions.)

---

### Post by haxer on 2006-09-11
what is Wifi-radar?

---

### Post by Metacarpal on 2006-09-11
Wifi-radar is a wireless networking configuration tool.  Some people find it more useful than the standard gnome network-manager.

---

### Post by haxer on 2006-09-11
Ok sounds good :P if your using those things

---

