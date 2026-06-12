---
title: "[SOLVED] Compartir connexió internet"
date: 2007-10-21
forum: Catalan Team
---

### Post by manelolesa on 2007-10-21
Hola, estic intentant compartir la connexió d'internet entre dos Ubuntus.
He mirat pels foros i lo que mes he trobat es instalar el Firestarter i configurar-lo amb el wizard.
La configuració penso que la faix bé, l'Starter s'inicia be.
Pero no comparteixo internet i en l'ordinador que te la connesxió també em quedo sense connexió.
Alguna idea.

---

### Post by manelolesa on 2007-10-22
Ja ho tinc solucionat.
El Firestarter interactua amb el DHCP-SERVER i per defecte li posa un rang de IP'S 168.1.100.0/254 . Jo tenia ip's fixes i estaven fora d'aquest rang. He canvia les  IP'S per que estiguin dins del rang 168.1.100.0/254 i tot OK.

Salut

---

