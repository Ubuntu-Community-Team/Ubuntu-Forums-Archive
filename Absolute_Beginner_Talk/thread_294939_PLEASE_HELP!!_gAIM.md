---
title: "PLEASE HELP!! gAIM"
date: 2006-11-07
forum: Absolute Beginner Talk
---

### Post by billybag on 2006-11-07
in an effort to upgrade to the new gaim beta, i ****** something up.

added and updated my repositories:
deb [http://repository.debuntu.org/](http://repository.debuntu.org/) dapper multiverse
deb-src [http://repository.debuntu.org/](http://repository.debuntu.org/) dapper multiverse

i then tried to dl the new gaim through terminal:
sudo apt-get instal gaim

no luck so i decided to try synaptic package manager.
the upgrade from my original 1.5 version was available, however it would not upgrade. i got this message:
gaim:
 Depends: libavahi-compat-howl0 (>=0.6.0) but it is not installable
  Depends: libcairo2 (>=1.0.2-2) but 1.0.2-0ubuntu1.1 is to be installed
 Depends: libdbus-1-2 (>=0.60) but it is not installable
 Depends: libdbus-glib-1-2 (>=0.60) but it is not installable
  Depends: libfreetype6 (>=2.1.10-1) but 2.1.7-2.4ubuntu1.2 is to be installed
  Depends: libgcrypt11 (>=1.2.2) but 1.2.1-3 is to be installed
  Depends: libglib2.0-0 (>=2.10.0) but 2.8.3-0ubuntu1 is to be installed
 Depends: libmeanwhile1 (>=1.0.0) but it is not installable
  Depends: libpango1.0-0 (>=1.12.3) but 1.10.1-0ubuntu1 is to be installed

so i tried just updating the gaim-data.
Well now all my gaim stuff is UNINSTALLED and i cannot install it.
PLEASE help!!!!


EDIT* Okay i just took out the previous said repositories and then reloaded synaptic and then installed gaim. this worked.

so at least i have gaim again, but i really would like the new gaim beta (mainly because of research showing that this versions's file transfers and direct connects work)

---

### Post by zek725 on 2006-11-07
The new **Gaim** is available in Edgy Eft. :)

---

### Post by ner0tic on 2006-11-07
add the edgy repos then apt-get update then apt-get install gaim

---

### Post by sethmahoney on 2006-11-07
I believe you can get the new GAIM beta using Automatix as well.

---

