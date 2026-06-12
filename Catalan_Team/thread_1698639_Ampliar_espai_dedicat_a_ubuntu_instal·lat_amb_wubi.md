---
title: "Ampliar espai dedicat a ubuntu instal·lat amb wubi"
date: 2011-03-02
forum: Catalan Team
---

### Post by jfabregat on 2011-03-02
Bones,

vaig instal·lar l'ubuntu amb wubi i m'he quedat sense espai, es pot ampliar l'espai dedicat a l'ubuntu?

Gràcies,

Jordi

---

### Post by wgarcia on 2011-03-02
Es pot fer reduint l'espai dedicat a altres sistemes operatius i incrementant l'espai dedicat a ubuntu, però primer has de defragmentar dos cops almenys el windows, i fer còpia de totes les dades perquè no s'ha de perdre res però per si un cas. 

El programa que s'utilitza per canviar de dimensió les particions es diu gparted. Un cop instal·lat apareix al menú sistema. 

Quan es redueix la dimensió d'una partició això allibera un espai del disc que queda sense assignar, i es pot incrementar a continuació la partició contigua a aquest espai. 

Primer s'ha d'assegurar que queda clar quines  són les  particions on són el Windows i on és Linux (es pot veure pel sistema de fitxers que normalment són "ntfs" i "ext4" respectivament per a Windows i per a Linux. 

gparted és força intuïtiu però remoure particions pot generar fàcilment pèrdua de dades i s'ha de saber el que s'està fent.

---

### Post by jfabregat on 2011-03-03
Merci,

però com he instal·lat l'ubuntu amb wubi no tinc partició en disc, no es pot ampliar el tamany de l'arxiu dedicat a l'ubuntu?

---

### Post by wgarcia on 2011-03-03
Ah, d'acord, mai no he instal·lat amb wubi, no sé com es fa en aquest cas.

---

