---
title: "Brutícia i demés"
date: 2010-02-17
forum: Catalan Team
---

### Post by Lem_Pv on 2010-02-17
Hola, després de molt de temps em passe per ací, ja que tinc un dubte que no em deixa dormir per les nits. :sad: xD

Quan instal·lem un programa pot ser estem instal·lant amb ell dependències a banda del programa, el cas és, com borrar-les sense endur-me'n d'altres valides?

Per exemple:

L'altre dia vaig instal·lar està utilitat, que oferix l'efecte exposeé del MacOS sense quasi utilitzar recursos:

[http://fausto23.wordpress.com/2009/02/03/conseguir-efecto-expose-en-ubuntu-sin-compiz/](http://fausto23.wordpress.com/2009/02/03/conseguir-efecto-expose-en-ubuntu-sin-compiz/) (en castellà)

La cosa és que el programeta no em fa el pes i ara vé lo bò. Com borre tot el que he instal·lat, dependències incluides? Sé que per borrar una carpeta es sudo rm -rm, però que faig amb lo altre? No m'agrada tindre llibreries (o el que siguen) per ahí que no van a utilitzar-se per a res escampades pel sistema operatiu.


No sé si és una xorrada o una mania, però gràcies! ;)

---

### Post by papapep on 2010-02-17
Per desinstal·lar paquets instal·lats amb el dpkg, l'apt-get o l'aptitude, cal emprar la mateixa ordre amb el modificador corresponent.

Per exemple, si instal·lem el paquet1 que té com a dependència dep1 i dep2:

```
sudo aptitude install paquet1
```

per a eliminar-los completament tots, cal fer:

```
sudo aptitude purge paquet1 dep1 dep2
```

i el sistema de gestió de paquets se n'encarregarà de tot.

Lem_Pv: si us plau, cal posar un títol als fils que sigui el màxim de descriptiu del contingut de la consulta. Un "instal·lació i desinstal·lació de paquets", p. ex., hauria estat prou més il·lustratiu que "Brutícia i demés" que sembla que parli d'altres coses.

---

### Post by Lem_Pv on 2010-02-19
Gràcies, ho he provat i ara per ara tot funciona com toca. A l'estar borrant llibreries gràfiques pensava que pot se m'emportava sense voler algunes de l'entorn gràfic, com moltes vegades m'ha passat.

Per lo del titol disculpa, era una cosa tant bàsica que no savia com expressar-la.

---

