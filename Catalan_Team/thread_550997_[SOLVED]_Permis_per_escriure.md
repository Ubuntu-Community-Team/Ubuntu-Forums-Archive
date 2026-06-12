---
title: "[SOLVED] Permis per escriure"
date: 2007-09-14
forum: Catalan Team
---

### Post by Mitjons on 2007-09-14
M'acabo de comprar un disc dur extern (Iomega) per USB. L'he formatejat a ext3. Després de reiniciar se'm munta tot sol però no em deixa escriure per que no tinc permis de Root :confused:

Que he de fer per tenir el meu permis per escriure?

---

### Post by patrickfromspain on 2007-09-14
sudo chmod 777 /punt-de-muntatge

---

### Post by Ferri on 2007-09-14
> sudo chown -R el_teu_usuari /cami/al/disc 
Amb això faràs que el propietari del disc sigues tu.
Si encara no et deixa escriure:
> chmod -R +rw /cami/al/disc
Amb això hauries de tenir permís de lectura i escriptura.

---

### Post by Mitjons on 2007-09-14
Moltes merces 
Finalment ho he solucionat, o això sembla, d'una forma una mica més barroera; **sudo nautilus** i canviant els permisos del disc com a root per a tothom :lolflag:

Ja estava preocupat per que el etc/ftab no em funcionava

---

### Post by orestesmas on 2007-09-15
Jo diria que si el teu usuari pertany al grup "plugdev", hauries de poder escriure-hi sense fer coses rares addicionals.

---

