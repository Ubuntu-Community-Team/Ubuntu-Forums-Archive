---
title: "Error amb la instal-lacio de un paquet"
date: 2007-08-27
forum: Catalan Team
---

### Post by carlesbm on 2007-08-27
Hola companys.

     El dissabte vaig instal-lar, se suposa que ho vaig fer un programa al meu Ubuntu 7.04 hem va donar un error que ara no recordo, pero desde aquell moment cada cop que vull arrancar el gestor de paquetes  ho instal-lar alguna aplicaió m'apareix el següent error, us adjunto una imatge de la pantalla, doncs una imatge val mes que mil paraules.

    Com puc fer per eliminar aquesta aplicació, doncs no m'interessa. En la versio 6 de Ubuntu es podia editar un fixer de paquets, però en aquesta no ser com fer-ho.

Moltes gracies

---

### Post by pespin on 2007-08-27
provar amb 
```
sudo aptitude update; sudo aptitude purge facturelinex
```

---

### Post by carlesbm on 2007-08-27
Hem dona un misstge que ho he de arregalar manualment , però com?

---

### Post by papapep on 2007-08-27
No sé si serà el mateix cas, però sembla que el paquet facturlinex té un problema amb una dependència amb el mysql.
Aleshores una possible solució seria, en un terminal fes:

```
sudo touch /etc/init.d/mysql
```

Un cop fet això, prova a carregar-te el facturlinex:

```
sudo aptitude purge nomdelpaquet
```

Si es resisteix, prova a reinstal·lar-lo primer i després esborrar-lo amb la comanda anterior.

Carles: el missatge de la segona impressió de pantalla indica que no has executat la comanda sense drets de superusuari.

---

### Post by papapep on 2007-08-27
Per cert Pespin, potser et funcioni enllaçar ordres amb ";", però no és una manera gaire ortodoxa. La "formal" és ficar-hi "&&" enmig:

```
sudo aptitude update && sudo aptitude install paquet
```

---

### Post by carlesbm on 2007-08-27
Hola altre cop

     No hi ha manera de treure aquest programa :( ja estic un amica desesperat.

     Ha més ara estic intentant de instal_lar un altra aplicació i també hem trobo amb problemes Uffff si euq es complicat aquest S.O. estem massa mal acostumats amb el Windows.

   Si no puc eliminar aquest programa poder torni ha instal-lar Ubuntu de nou.

Gracies

---

### Post by pespin on 2007-08-27
> Per cert Pespin, potser et funcioni enllaçar ordres amb ";", però no és una manera gaire ortodoxa. La "formal" és ficar-hi "&&" enmig:

Havia vist utilitzar l'altre, però no sabia k era mes "legal" diguem-ne. Me l'apunto, merci pel consell :)


Carlesbm recordo k hi havia una opció del APT del tipus "sudo dpkg-reconfigure" k potser et serveix, ja que servia per desentortolligar embolics d'aquests

---

### Post by carlesbm on 2007-08-27
Hola 

     Us deixo aquest ultim missatge per si hem podeu ajudaar ha desfer aquest embolic.

    He trobat en un forum informació sobre la instal-lació d'aquesta aplicació i crec que he embolicat la meva instal-lació l'adreça es:

[http://www.gnulinex.net/smf/index.php?topic=5520.0](http://www.gnulinex.net/smf/index.php?topic=5520.0)

Demà procediré ha reinstal-lar el sistema.

Gracies per la vostra ajuda

---

### Post by CarlesOriol on 2007-08-29
Estas a la consola com a root i fas sudo?

Per impersonar qui?

---

