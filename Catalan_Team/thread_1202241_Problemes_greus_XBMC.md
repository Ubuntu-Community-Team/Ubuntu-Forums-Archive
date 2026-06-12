---
title: "Problemes greus XBMC"
date: 2009-07-02
forum: Catalan Team
---

### Post by akyra on 2009-07-02
Hola a tothom,

Ahir un company em vadir que provés el XBMC, el servidor de mitjans digitals, i bé, vaig instal·lar-lo, i aquest matí tinc la sorpresa de que directament es comença a engegar l'ubunt, però en lloc de demanar l'usuari d'ubuntu per entar normalment, directament s'engega el XBMC.

Jo només vull tenir el XBMC per poder utilitzar-lo a vegades i executar-lo quan jo vulgui, però de cap manera volia que s'engegui tal com engego l'ordinador.

Com ho puc solucionar i deixar-lo com estava?

Gracies.

---

### Post by akyra on 2009-07-02
Bé, he fet un apt-get remove xbmc-live xbmc, i finalment un apt-get autoremove xbmc i ja està desinstalat, el problema és que ara quan s'engega el ubuntu comença a carrgar normalment fins que hauria de demanar el ususari i password normal de ubuntu, a les hores m'apareix la consola i em demana el usuari, però en modo consola.

Com puc recuperar el modus gràfic que tenia abans?

Moltes gracies.

---

### Post by papapep on 2009-07-02
Per Gnome:
```
sudo aptitude install gdm
```

Per KDE:
```
sudo aptitude install kdm
```

---

### Post by akyra on 2009-07-03
Gracies, però ahir a la tarda vaig formatejar la partició "/" i vaig tornar a tenir funcionant l'ubuntu com el tenia.

Suposo que aquestes instruccions tornan a instal·lar l'escriptori gnome o kde.

Ho tindré en compte per futures pifies.

Ara intentaré tornar a instalar-lo, però no des dels repositoris sino el paquet dpkg, així sabre que instal·lo.

Salutacions.

---

### Post by papapep on 2009-07-03
Crec que tindràs bastants més problemes fent-ho així. Per saber què instal·les, només et cal mirar-te els missatges que et mostren els programes gestors de paquets (siguin gràfics o no). Fer-ho manualment pot ser útil per practicar, però també et pot portar molts maldecaps.

---

