---
title: "problemes amb VMware i 10.10"
date: 2010-12-06
forum: Catalan Team
---

### Post by tuca toco on 2010-12-06
Hola per algun software antic haig de tenir un petit xp virtualitzat amb vmware. fins al 10.04 tot a anat be però ara amb el 10.10 diu que s' ha actualitzar, i al actualitzar-se dona un error.

Unable to build kernel module.

See log file /tmp/vmware-root/setup-2264.log for details.

us adjunto el fixer setup... que em podeu ajudar, ara el que he hagut de fer es reinstal.lar el 10.04 a una altra partició per poder treballar amb l' Vmware.

Salutacions, David

---

### Post by wgarcia on 2010-12-06
Tens instal·lat els fitxers capçalera (linux-headers) per al teu kernel? Pots provar des d'una terminal:

sudo apt-get install build-essential

i reiniciar el sistema a veure si es recompilen els mòduls de vmware.

---

### Post by tuca toco on 2010-12-06
Fet... segueix igual :-(

---

### Post by wgarcia on 2010-12-07
Sembla que en aquest enllaç:

[http://www.debuntu.org/how-wmware-workstation-7.1-ubuntu-maverick-meerkat-10.10](http://www.debuntu.org/how-wmware-workstation-7.1-ubuntu-maverick-meerkat-10.10)

expliquen com arreglar el mòdul que no et va. Si vols intentar-ho i te'n surts, explica aquí fins a on arribes a veure si pots arribar a arreglar-ho.

---

### Post by tuca toco on 2010-12-08
gracies...

he seguit les passes de l'enllaç:

tar -xzvf vmware-7.1-ubuntu10.10-patch.tar.gz
cd vmware-7.1-ubuntu10.10-patch
sudo ./apply_patch.sh

s' ha actualitzat sense problemes i a arrancat el programa.

---

### Post by wgarcia on 2010-12-08
M'alegro que se t'hagi arreglat. Pots posar "Solved" al fil clicant a "Thread tools" i escollint "Solved".

---

