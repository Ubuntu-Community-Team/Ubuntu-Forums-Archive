---
title: "wubi i w7"
date: 2012-10-03
forum: Catalan Team
---

### Post by Josep Maria on 2012-10-03
Tinc un ordinador eMachines amb el W7 preinstal.lat.
Vaig provar d'instal·lar  Ubuntu 12.04, però en reiniciar l'ordinador arrenca amb W7 sense opcions.
Vaig provar d'instal·lar Ubuntu amb el Wubi. No m'ha modificat cap partició, però em deixa accedir a W7 o Ubuntu, des d'un gestor d'arrencada de windows.
Podríeu dir-me quina diferencia hi ha entre instal·lar Ubuntu creant una partició ext4 o instal·lar-lo amb Wubi?
Com puc fer una instal·lació d'Ubuntu en una màquina que te quatre particions pre-configurades?

---

### Post by albandy on 2012-10-20
Wubi crea un sistema de fitxers virtual dins de la partició de windows. El problema amb això és que si la partició te alguna fallada, podría afectar a l'Ubuntu i no tornar a funcionar.

A la partició 4 que tens?
T'ho pregunto perque si es una partició de dades, podries copiar el contingut a una altra partició, eliminar-la i crear una nova partició extesa, on s'haurien de crear 3 particions lògiques, una per lo que tenies emmagatzemat, una altra per linux i una altra pel swap de linux.

---

### Post by Josep Maria on 2012-10-22
Gràcies Albandy: ho he fet, he creat una particio ext4/ una altra ext4/home i la partició swap a la particio 4.
Ara he pogut instal.lar l'Ubuntu 12,10 i funciona bé.

---

