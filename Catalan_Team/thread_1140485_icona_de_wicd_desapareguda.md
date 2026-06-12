---
title: "icona de wicd desapareguda"
date: 2009-04-27
forum: Catalan Team
---

### Post by climent on 2009-04-27
M'ha desaparegut la icona que s'obre quan s'ha instal·lat el wicd. Concretament és la icona de dos monitors amb una barra vertical, sembla que es diu "wicd tray icon 1.5.9". He reinstal·lat el wicd, l'he desinstal·lat i tornat a instal·lar, reiniciat després de cada tasca, i res de res. No és que tingui gaire importància, ja que tenim molts applets que ens indiquen el senyal, però és voldria tornar-lo a tenir.
Algú em pot fer la llum?

---

### Post by papapep on 2009-04-27
Has d'executar el

```
wicd-client
```

Si vols que surti el gestor de xarxes sense que surti l'icona a la barra d'applets, és amb:

```
wicd-client --no-tray
```

---

### Post by PatrickVogeli on 2009-04-28
aquesta me la se! instal·la el wicd que hi ha als repositoris de l'ubuntu, no el que te baixes de la web.

salut

---

### Post by climent on 2009-04-28
està instal·lat des de dipòsits, no de la web. Ja he executat wicd-client, i res. A més, el cas és que sortia, però no sé quin carai de maniobra he fet que ha estat quan m'ha desaparegut.

---

### Post by papapep on 2009-04-28
Pots purgar el paquet i tornar a començar, o buscar l'executable i fitxers de configuració i verificar que no tinguin cap problema de permisos.

Quan executes el wicd-client, (en un terminal, clar) quin missatge et mostra??

Per cert, en versions anteriors, en vers del wicd-client, havia un script en python a /opt/wicd que es deia tray.py, que era el de l'applet. No crec que hagin tornat enrera, oi??

---

### Post by climent on 2009-05-01
per a papapep: la carpeta que comentes existeix, però està buida. Finalment, per altres qüestions, he fet una instal·lació total i completa del Jaunty i, evidentment, en tornar a instal·lar el wicd ha aparegut la famosa icona.

---

