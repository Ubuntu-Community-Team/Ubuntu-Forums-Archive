---
title: "WiCD"
date: 2009-02-24
forum: Catalan Team
---

### Post by venusfenix on 2009-02-24
Buenas,

fa temps tenia problemas per conectar-me amb la wifi, desde que m'he instalat el wicd que no tinc problemes, l'unic, quan l'aplicacio s'actualitza, llavors, tinc que començar de nou.
Aquest ultim cop, ha sigut definitiu, no hi ha manera que es connecti, a mes, al ficar l'opcio WEP, a la barra que diu les fases de conexio es veu clarament que s'intenta conectar per WPA, o sigui, que l'ultima actualitzacio no es correcte, com tirar endarrere???

gracies,

---

### Post by papapep on 2009-02-24
Baixa't el paquet .deb de la versió que et funcionava correctament d'aquí:

[http://sourceforge.net/project/showfiles.php?group_id=194573&package_id=229460](http://sourceforge.net/project/showfiles.php?group_id=194573&package_id=229460)

Desinstal·la el wicd, instal·la la versió que t'has baixat, i un cop el tinguis configurat i funcionant correctament, fes servir les instruccions que trobaràs aquí:

[http://extralinux.net/?q=node/135](http://extralinux.net/?q=node/135)

per evitar que s'actualitzi sense que tu vulguis. :-)

**Afegitó:** Per cert, si en intentar desinstal·lar el Wicd et dóna un error et cal esborrar un fitxer:

```
sudo rm /var/lib/dpkg/info/wicd.prerm
```

i ja et deixarà desinstal·lar-lo sense problemes i continuar amb la resta del procés.

---

### Post by venusfenix on 2009-02-25
moltes gracies,
ho probaré.

moltes gracies!!!

---

### Post by venusfenix on 2009-02-26
Buenas,

he fet el que m'has dit, pero continu tenin el mateix problema, no se si, descarregar-me una versio encara mes antiga, per exemple, 1.5.7??

gracies

---

### Post by papapep on 2009-02-26
Jo a un dels meus ordinadors he hagut de baixar fins la 1.4.2, imagina't...

---

### Post by venusfenix on 2009-02-28
ja esta, al final la versio 1.5.5 ha guanyat, i he fet el que en deies per posar en hold en paquet, pero no en funciona. perque??
he posat: sudo apt-get hold wicd
potser el nom del paquet no es el correcte??
en el terminal, em possaba que un paquet posat en hold i per no mantenir, pero en el paque sinaptic continua?? potser quant re-inici la sessió??

moltes merces!!!!!

---

