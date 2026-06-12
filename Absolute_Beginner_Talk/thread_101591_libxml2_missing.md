---
title: "libxml2 missing"
date: 2005-12-10
forum: Absolute Beginner Talk
---

### Post by binks on 2005-12-10
ok hi im trying to install the latest version of kino as its supposed to import xvid but im getting dependency problems with libxml2 but i cant find this in the repository or doing a googgle search .
can someone pointr me in the right direction ta:p 
binks

---

### Post by codejunkie on 2005-12-10
[quote=binks]ok hi im trying to install the latest version of kino as its supposed to import xvid but im getting dependency problems with libxml2 but i cant find this in the repository or doing a googgle search .
can someone pointr me in the right direction ta:p 
binks[/quote]
you could try running ```
sudo apt-get build-dep kino
``` if that dosen't work you'll have to track down each dependency build and install them first.

---

### Post by binks on 2005-12-10
this will only pull in the dependecies for the repository version of kino not the latest release i think but i will try when i get home 
cheers

---

### Post by binks on 2005-12-10
ok so i was wrong again you got it right it worked a treat cheers

---

### Post by binks on 2005-12-10
anyone worked out how to import xvid files into kino 
i have 0.8.0 so it should

---

### Post by gord on 2005-12-10
you'll need to install the development files for libxml2, which just so happen to be called libxml2-dev

```

sudo apt-get install libxml2-dev

```

try ./configure (i assume) again and if you get more dependancy problems just take the general name (like libxml2 or whatever) and do a search for it in synaptic, generally the development files will be in the same <libname>-dev format.

---

