---
title: "Grub amb Ubuntu i Windows en dos discos diferents"
date: 2007-04-24
forum: Catalan Team
---

### Post by jraulbc on 2007-04-24
Hola de nou,

Primer de tot, com que feia uns dies que no llegia el fòrum, felicitats a la comunitat pel Feisty. Ja m'he actualitzat i hem sembla fins i tot que l'ordinador va més ràpid!

La meua consulta és, tinc en el disc dur principal Ubuntu i en el secundari vaig instal·lar Windows XP a vore si podia usar-los tots dos alhora (hi ha alguns programetes que no he pogut fer anar amb wine). Vaig buscar per ahí com modificar el grub i al final açò és el que he provat, però no em funciona:

(després de totes les línies que fan referència als kernels)

    title Microsoft Windows XP
    rootnoverify (hd1,0)
    makeactive
    chainloader +1

Quan inicia el sistema, trio l'XP de la llista i apareix

    starting up...

però d'ahí no passa.

Alguna suggerència?

Gràcies per endavant!

---

### Post by angelmartinezn on 2007-04-27
Assegurat que la linia de rootnoverify(hd1,0) és correcte, tingues en compte que grub comença a contar els discs desde l'hd0 (si no m'equivoco).

A mi m'ha passat de tant en quant això mateix (sóc un despistat), i el que he fet de vegades quan no tinc ni temps ni ganes de pensar és crear diverses entrades al grub, totes iguals i entre elles només es canvia la partició (segon paràmetre de rootnoverify).

També un altre opció seria investigar si tens el windows està preparat per arrencar desde el disc on el tens, i si la partició que el conté està com a partició d'arrencament predeterminada (activa).

espero haver-te ajudat (ni que sigui una mica)

Salut i força al canut!

---

