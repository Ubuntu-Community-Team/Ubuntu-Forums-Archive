---
title: "No puc instalar pacs d'icones"
date: 2009-05-11
forum: Catalan Team
---

### Post by tanreb20 on 2009-05-11
Avui he intentat instalar un paquet d'icones al meu ubuntu, quan tinc el tar.gz i l'arrastro fins la finestra de temas, aquesta es tanca directament i no s'instala.

Alguna sugerencia?

---

### Post by Xispa on 2009-05-14
Pots intentar de descomprimir l'arxiu tar.gz directament amb el Gestor d'arxius (botó dret del ratolí): t'hauria de sortir una carpeta (que habitualment coincideix amb el nom del tema) que conté, com a mínim, una subcarpeta amb nom gtk-2.

Si còpies la carpeta que s'ha generat en descomprimir a /usr/share/themes, quan tornis a arrancar el gestor de temes ja t'apareixerà.
Si es tractés d'un tema d'icones, podries fer el mateix, però en aquest cas, fent la còpia a /usr/share/icons.

Un truquet: si vols conservar els temes entre instal·lacions i tens la home en una altra partició, pots fer el mateix, però fent les còpies a /home/{nom_usuari}/.themes i /home/{nom_usuari}/.icons

---

