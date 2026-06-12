---
title: "Getting sound to work?"
date: 2006-04-24
forum: Absolute Beginner Talk
---

### Post by Just4 on 2006-04-24
I've been trying but I can't seem to get sound to work, with either my onboard sound (C-Media CMI8738) Or my addon card (Ensoniq ES1370 PCI card) should I try another card or what? (Note that I am using Xubuntu)

---

### Post by souteneur3190 on 2006-04-24
this might be a lil drastic, but try gnome or download automrix and use the sound fix.

---

### Post by Just4 on 2006-04-24
I have a C-Media 8738 also, and when googling turns up that its a good card for Linux (It has official drivers, etc) how would I install it?

---

### Post by xXx 0wn3d xXx on 2006-04-24
[QUOTE=Just4]I have a C-Media 8738 also, and when googling turns up that its a good card for Linux (It has official drivers, etc) how would I install it?[/QUOTE]
In terminal (Applications > Acessories > Terminal) type:

> sudo alsamixer

Make sure nothing is muted or turned down very low. If that doesn't work, you may have to upgrade your kernel but try the first method.

---

### Post by Just4 on 2006-04-25
Got it working with my C-Media 8738 out of the box, very good card for Linux. (Very cheap too, paid $8 for it.) - Thanks for all the help.

---

