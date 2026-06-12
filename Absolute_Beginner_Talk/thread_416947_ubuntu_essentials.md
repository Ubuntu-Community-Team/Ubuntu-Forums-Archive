---
title: "ubuntu essentials?"
date: 2007-04-21
forum: Absolute Beginner Talk
---

### Post by doubleuicked on 2007-04-21
hey guys,

a total beginner to ubuntu 7.04, what are some essential installations/upgrades that i should apply?


cheers

---

### Post by halitech on 2007-04-21
for me it was to make sure all hardware worked first (video settings, sound, network) then multimedia programs and codecs then K3B (burning) and then my video apps (Devedee and mandvd). 

It really depends on what you will be doing with your system

---

### Post by SOULRiDER on 2007-04-21
What i allways install is Flash, MP3 support, video codecs, NVidia drivers and Java jdk (for prgoramming in java)

---

### Post by vanadium on 2007-04-21
My answer is: there are no essentials. The default Ubuntu installation just works right out of the box. That is the great strength of Ubuntu. Additional installs are required only if you have specific needs that are not coming with the default install. These needs are very individual, though.

---

### Post by zvacet on 2007-04-21
Aside of all codecs,players basic things you need are build-essential and alien.With build-essential you will be able to compile programs and with alien you can convert rpm file to deb.
Build-essential ison the CD so 
```
sudo apt-cdrom add
```
```
sudo aptitude build-essential
```

Alien is in synaptic.

---

### Post by Sef on 2007-04-21
For build-essential, you can just type ```
sudo aptitude install build-essential
``` and it will ask you to install the Ubuntu cd.

---

