---
title: "Barres de gnome desaparegudes"
date: 2007-05-31
forum: Catalan Team
---

### Post by crazyserver on 2007-05-31
Bé... no espero trobar gaires respostes al meu problema ja que es d'aquests raros raros...

quan arrenco l'ordinador i es carrega el meu usuari, de manera totalment aleatòria, el gnome decideix carregar o no les barres de dalt i baix i ho fa de la següent manera, a vegades carrega la de dalt, a vegades carrega les dues... o a vegades cap... la de baix sola no l'he vist mai fins ara, i si no es carreguen, no tinc barres, de moment la solució d'ara és tornar a entrar amb l'usuari o més al o bestia, reiniciar les X.

Fa bastant de temps que em passa i la veritat no se ni des de quan i perquè m'ho fa... no es que em molesti però potser trobo algú més que li passa i podem trobar solucions...

Per començar provaré amb un altre usuari...#-o

---

### Post by patrickfromspain on 2007-05-31
el que jo faria:

cambiar el nom a les carpetes .gnome, .gnome2 i .config i despres sudo apt-get install --reinstall gnome-panels. Si no funciona sempre pots restaurar aquestes carpetes i en paus. Vigila, que suposo que perdras alguna configuracio de l'escriptorio i les barres.

salut!

---

### Post by MarkCat on 2007-05-31
si et serveix de consol a mi també em passa.
em deu passar un cop de cada 20 que engego el pc...

---

### Post by crazyserver on 2007-06-01
Provaré la proposta del patrick quan tingui una estona, i sí, em consola no ser l'únic, això vol dir que trobarem la solució :D

---

### Post by crazyserver on 2007-06-05
Bé gràcies per totes les aportacions, ja he resolt el cas. Gràcies al patrickfromspain vaig proaar-ho i després de veure que amb les barres buides tot anava, vaig restaurar el que tenia i vaig anar més enllà.
MIrant un log vaig trobar un warning al carregar el Tomboy i... BINGO! sense el Tomboy a la barra va tot correctament i a la primera!

El que ara estic fent és tornar-lo a posar a veure que passa... i de moment m'apareixen bé.

Per tant el resultat al cas és treure el Tomboy de la barra.

MarkCat... tens tu el Tomboy posat?

---

