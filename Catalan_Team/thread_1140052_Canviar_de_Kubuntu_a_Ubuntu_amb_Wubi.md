---
title: "Canviar de Kubuntu a Ubuntu amb Wubi"
date: 2009-04-27
forum: Catalan Team
---

### Post by tonidal on 2009-04-27
Hola!

Sóc novell en linux, tinc un netbook i hi he instal·lat Kubuntu amb Wubi (compartint disc dur amb XP). La primera impressió és que la pantalla és massa petita per gestionar amb comoditat tot el que ofereix Kubuntu i m'interessaria saber si és possible canviar a Ubuntu des del propi Kubuntu (tal com crec que es pot fer en les instal·lacions normals) o si he d'eliminar la instal·lació actual i repetir el procés amb Wubi demanant que instal·li Ubuntu.

I una segona pregunta: amb Wubi es pot disposar simultàniament dels dos escriptoris gnome i kde per comprovar quin s'adapta millor als meus gusts i al meu Acer Aspire One? En cas afirmatiu, ocuparia molt espai?

Salutacions i moltes gràcies

---

### Post by Albert Segura on 2009-04-27
No he provat mai el wubi, però suposo que no tindràs cap problema per instal·lar els dos escriptoris. 
Per instal·lar Gnome (o un altre): Sistema > Administració > Synaptic i alla: Editar > Marcar paquets per tasques.
O directament:
> sudo aptitude install gnome-desktop
O no se si es:
sudo aptitude install gnome

no se si em deixo res ;)

---

### Post by papapep on 2009-04-27
Hola, Toni.

En principi, tal i com et comenta l'Albert, amb un:

```
sudo aptitude install ubuntu-desktop 
```

hauries de poder triar a l'arrencada si vols emprar Gnome o KDE o qualsevol altre entorn d'escriptori que instal·lis a la partició amb l'Ubuntu. 
Amb el Synaptic el funcionament és semblant, marques el paquet ubuntu-desktop i li dius que apliqui el que has demanat. :)

Respecte el que ocupa l'entorn, amb l'aptitude, abans de dir que sí, fes un cop d'ull al missatge que et mostra que inclou la mida del que descarregues, i la mida que ocuparà un cop instal·lat. Suposo que el Synaptic deu mostrar alguna cosa semblant, però com que no el faig servir, doncs no sé on ho diu.

---

