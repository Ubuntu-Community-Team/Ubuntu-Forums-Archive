---
title: "opera install problems"
date: 2007-10-28
forum: Absolute Beginner Talk
---

### Post by froggger on 2007-10-28
i can't install opera on gutsy, when i do i get this message
"Depends: libqt3-mt (>=3:3.3.8really3.3.7) but it is not installable"
but i can't install libqt3-mt, so what do i do?
thanks!

---

### Post by overdrank on 2007-10-28
> **froggger said:**
> i can't install opera on gutsy, when i do i get this message
"Depends: libqt3-mt (>=3:3.3.8really3.3.7) but it is not installable"
but i can't install libqt3-mt, so what do i do?
thanks!

 Hi and , I would recommend check and make sure all your repos are enabled. System, administration, software sources.

---

### Post by n3tfury on 2007-10-28
give a little more info and let us know HOW you're trying to install opera.

---

### Post by zvacet on 2007-10-29
**Right click on Opera package>Gdebi installer**.That is all you have to do.

---

### Post by FredB on 2007-10-29
Yes. Gdebi will download any single package needed.

---

### Post by davesmith on 2007-10-29
Opera installed just fine on my gutsy system.
 
You might need to make sure that all your repositories are enabled:-
 
Code:
gksudo gedit /etc/apt/sources.list
 
This will bring up your sources.list. First unhash any entries that start with #deb and save, then try
 
code:
sudo apt-get update
sudo apt-get install opera
 
if that still wont work, you might need to add the following to your sources.list
 
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner
 
save and try
 
sudo apt-get update
sudo apt-get install opera
 
again and it should d/l and install

---

