---
title: "Es pot establir una prioritat entre targetes de xarxa?"
date: 2009-08-16
forum: Catalan Team
---

### Post by lpargemi on 2009-08-16
Hola

Estic posant apunt un portàtil amb jaunty, i per ara tot va bé, però tinc un dubte:

La màquina té una targeta de xarxa per cable (eth0) i una amb wifi (wlan0). Em funcionen tots dos bé, però jo voldria definir que quan tots dos canals estiguin operatius les dades s'enviïn per la xarxa de cable, que és més ràpida.

Pot fer-se això?

Agraït

Lluís

---

### Post by socderafel on 2009-08-16
si vols gastar ethernet, deshabilita la inhalambrica, i si vols gastar la inhalambrica, deshabilites l'altra. O simplement desconnecta la xarxa inhalambrica a la que estigues connectat, i la estableixes com a manual...
fent click a l'icona de NetworkManager et surten les dos opcions.

---

### Post by lpargemi on 2009-08-17
> **socderafel said:**
> si vols gastar ethernet, deshabilita la inhalambrica, i si vols gastar la inhalambrica, deshabilites l'altra. O simplement desconnecta la xarxa inhalambrica a la que estigues connectat, i la estableixes com a manual...
fent click a l'icona de NetworkManager et surten les dos opcions.

Hola Socderafel, aquesta ja me la sabia. I funciona. Només que de tant en tant s'obren finestretes demanant els codis de validació de les xarxes wifi. 

La pregunta és per si hi ha algun mètode diguem-ne més elegant.

Agraït per l'interès.

Lluís

---

### Post by papapep on 2009-08-17
A banda de si algun programa ho fa o no, fet que no sé, això es podria fer amb un script que controlés si les interfícies són actives o no i, en funció de tot plegat, modifiqués l'enrutat de l'interfície i la configuració de la xarxa. Tot plegat, un bon exercici de programació d'scripts :)

---

### Post by socderafel on 2009-08-17
> **papapep said:**
> A banda de si algun programa ho fa o no, fet que no sé, això es podria fer amb un script que controlés si les interfícies són actives o no i, en funció de tot plegat, modifiqués l'enrutat de l'interfície i la configuració de la xarxa. Tot plegat, un bon exercici de programació d'scripts :)

Ara decideixes tu... jajajaja ...

---

### Post by CarlesOriol on 2009-08-18
Segurament ja ho estas fent:

Fes 

ip route list

Els valors metric més baixos indiquen major prioritat i no s'usaran les dues interficies si no està activat algun tipus de balanceig de càarrega (no és fàcil de fer per tant no pateixis que no ho tens).

Segurament et mostrarà la interficie eth0 amb metrica 1 i la wlan amb 2.

Si no sols et cal una comanda per canviar la metrica  ( ip route replace dev.... metric x ).

---

### Post by lpargemi on 2009-08-19
> **CarlesOriol said:**
> 

ip route list

Els valors metric més baixos indiquen major prioritat i no s'usaran les dues interficies si no està activat algun tipus de balanceig de càrrega (no és fàcil de fer per tant no pateixis que no ho tens).

Segurament et mostrarà la interficie eth0 amb metrica 1 i la wlan amb 2.

Si no sols et cal una comanda per canviar la metrica  ( ip route replace dev.... metric x ).

Pel què veig funciona així com dius, sempre que ho he mirat (des de què sé com fer-ho) em dona que estic connectat per cable a través de l'enrutador (adreça 1.1)

```
eva@eva:~$ ip route list
192.168.1.0/24 dev eth0  proto kernel  scope link  src 192.168.1.39  metric 1 
192.168.1.0/24 dev wlan0  proto kernel  scope link  src 192.168.1.38  metric 2 
169.254.0.0/16 dev eth0  scope link  metric 1000 
default via 192.168.1.1 dev eth0  proto static 

```

El tema dels scripts... potser quan sigui més gran...

Agraït

Lluís

---

