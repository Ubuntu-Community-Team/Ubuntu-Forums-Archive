---
title: "videocàmera no detectada"
date: 2009-04-20
forum: Catalan Team
---

### Post by climent on 2009-04-20
Tinc una càmera Samsung VP-D80, ordinador amb Firewire i Ubuntu Intrepid. He instal·lat el Kino i no aconsegueixo que el programa detecti la càmera. Primer tenia problemes amb els mòduls però jo diria que ara ja estan carregats. L'error que dóna el Kino és "no hi ha cap càmera compatible amb AV/C connectada o no està encesa" . Algú s'ha trobat amb el mateix, o en el seu defecte, podeu indicar alguna web o fòrum per consultar?

---

### Post by jaumell on 2009-04-20
A mi també em passava el mateix, ja des de la 7.10, si mal no recordo.

Em vaig tornar boig intentant descartar un problema de hardware, controladors, etc..

Finalment va resultar que era un bug del kino. Només permet la captura com a root.

Solucions (de més a menys cafre, crec):

executar kino com a root,
donar permisos al dispositiu raw1394,
afegir el teu usuari al mateix grup al que pertanyi el dispositiu.

Apart d'això, el kino sempre m'ha anat de fàbula! No entenc com encara seguim igual...

---

### Post by quitus on 2009-04-22
sempre podeu provar el kdenlive que es fabulós, i en la seva versió 0.7.3 (jaunty) impressionant, puc veure vídeos amb els efectes d'escriptori activats i tot.

salut

---

### Post by climent on 2009-04-23
El provaré, he cercat per la xarxa i només trobo referències de kino i cinelerra. Encara que kdenlive és del KDE i jo utilitzo GNOME, el provaré igual. Això sí, precisament avui dijous 23 és el dia de Jaunty. Primer m'actualitzaré i després aniré pel Kdenlive, a veure què tal.

---

### Post by quitus on 2009-04-24
> **climent said:**
>  precisament avui dijous 23 és el dia de Jaunty. 

Vaja, jo pensava que era el dia de sant Jordi...:P

---

