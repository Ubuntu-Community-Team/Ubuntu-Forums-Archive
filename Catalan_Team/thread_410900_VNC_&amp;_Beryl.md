---
title: "VNC &amp; Beryl"
date: 2007-04-16
forum: Catalan Team
---

### Post by basdala on 2007-04-16
Bona tarda companys,
He llegit que hi ha problemes amb VNC i Beryl (no es veu l'escriptori, es penja, etc etc...), però és que en el meu cas ni tan sols arriba a connectar.

Un cop he estat a casa he arrencat el vncviewer localhost:0 y m'ha donat un Connection reset by peer.

Alguna idea? Us ha passat abans? Sabeu d'alguna web meravellosa on algú ho hagi solucionat?

Mercès!

---

### Post by CarlesOriol on 2007-04-16
Jo no et recomanaria de mesclar vnc i beryl. L'ample de banda emprat per les transparencies i animacions pot fer que el sistema sigui totalment inútil.

---

### Post by basdala on 2007-04-19
Estic comdemnat a fer servir ssh per connectar a casa des de la feina, llavors? Quina gràcia. De tota manera, no crec que les transparencies afectin massa al resultat, total, el VNC només fa "pantallazos" i els envia per la xarxa, res més.

Cap altre escritorio remoto que pugui fer servir en lloc de l'VNC?

---

### Post by patrickfromspain on 2007-04-19
desconectar beryl no es una opcio? Abans de marxar selecciones metacity i ja esta.. son 2 segons.

---

### Post by orestesmas on 2007-04-22
Com a protocol de connexió remota el NX no té rival, i també usa ssh.

---

### Post by basdala on 2007-04-23
Resulta, nois, que quan he actualitzat a Feisty l'VNC a passat a funcionar fantàsticament bé. Té collons l'assumpte.

El cas es que ara passa que no sé si són paranoies meves o què, però si tinc el vino-server en marxa (l'escriptori remot) el Beryl comença a ralentitzar-se mooooooooooooolt al cap d'un temps. Fent-li un kill al vino-server reviu el Beryl completament.

Ara he desactivat l'escriptori remot, crec que tindré prou amb el SSH, però té un comportament molt curiós. Ningú més ha observat aquesta peculiaritat o, com deia, són paranoies meves?

---

