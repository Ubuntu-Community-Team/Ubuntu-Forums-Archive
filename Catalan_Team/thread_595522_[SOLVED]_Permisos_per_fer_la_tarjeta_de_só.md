---
title: "[SOLVED] Permisos per fer la tarjeta de só"
date: 2007-10-28
forum: Catalan Team
---

### Post by guillemsola on 2007-10-28
Com em va apuntar en papapep a un altre post:

> Amb els dos comentaris que fas sobre els missatges d'error amb el lspci i intentant accedir a Sistema > Preferències > So té pinta de que tinguis un problema de permisos.
L'usuari que fas servir és el que vas crear en instal·lar, o és un que has creat posteriorment??

Doncs sembla que efectivament el meu usuari migrat de festy a gutsy   ha perdut pel camí els permisos per fer servir la targeta de so pci "bona" i  es conforma amb una soundblaster. És curió pq tinc un altre usuari migrat de festy al pc i aquest "ha estat més llest" i no els perdut!

Això es pot arreglar?? Pel que he vist el meu usuari te permís per accedir a recursos de so. Com ho he d'enfocar per poder re-assignar els permisos d'un dispositiu pci a un usuari?

Salut!

---

### Post by guillemsola on 2007-10-30
Ara si que ja tinc l'ubuntu recuperat al 100%. La tarja de so principal que no sonava ja torna a anar bé :lolflag: :lolflag: :lolflag: :lolflag: :lolflag:

He trobat la resposta a un dels fòrums internacionals. Diu que no ho consideren un bug però deunido.

Després de reiniciar el Gutsy deia que fes un 

asoundconf set-default-card

i no va funcionar. Tal com diuen al fòrum primer cal borrar  els arxius que hi ha a l'usuari .asounrc perquè així es crein satisfactoriament els nous.

Per quant han dit que bé el Hoary??

Salut!

---

### Post by jodufi on 2007-10-30
La següent versió serà la Hardy Heron (la Hoary ja va passar fa dos anys), i la tindràs aquí a l'abril.

---

