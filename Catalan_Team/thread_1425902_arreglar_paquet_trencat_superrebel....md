---
title: "arreglar paquet trencat superrebel..."
date: 2010-03-09
forum: Catalan Team
---

### Post by trinkus on 2010-03-09
Hola,

He fet una actualitzacio i s'ha detectat un paquet trencat (flashplugin-nonfree). El cas és que no el puc reparar (el sistema em diu que el reinstali si el vull desinstalar) pero el synaptic no em deixa instalar-lo ni desintalar-lo i fins he provat amb 
sudo -r --force-remove-reinstreq flashplugin-nonfree
però em segueix dient que el paquet està malmès i que el reinstali...

alguna idea? Perquè jo ja no sé què més fer...

---

### Post by oriolsbd on 2010-03-10
Hola,

Precisament fa un parell de dies vaig arreglar el mateix problema a un amic (i va costar força trobar la solució)... :-)   Ara mateix, no deus poder instal·lar cap paquet per culpa d'això, oi?

El problema en el seu cas provenia del fet que la seva instal·lació provenia d'un Ubuntu 8.04 (o 7.10, no ho recordo) i el FlashPlugin encara era molt antic (versió 9.xxxx), i no sabia actualitzar a partir d'una versió tan antiga. Comprova que és aquest el teu cas.

Si és així, el primer que cal fer, per si de cas, és arreglar el fitxer sources.list (per si encara hi ha alguna entrada que apunti a "hardy" o a "gutsy"). Per editar-lo, executa la comanda següent:

```
sudo gedit /etc/apt/sources.list
```

Si hi trobes alguna entrada on hi posi "gutsy" o "hardy", avisa'ns per dir-te què cal fer.

Un cop arreglat aquest fitxer (i amb un "sudo apt-get update" posterior per actualitzar la llista de paquets) vam arreglar el problema "enganyant" la BDD de l'apt-get per tal que es pensi que no està instal·lat. Primer, ens fem una còpia de seguretat d'aquesta BDD (que en realitat és un fitxer pla):
```
sudo cp /var/lib/dpkg/status /var/lib/dpkg/status.copia
```

Ara, edita el fitxer:
```
sudo gedit /var/lib/dpkg/status
```

Sobretot, si en algun moment fas alguna modificació en aquest fitxer que no tinguis clara, surt sense desar. En aquest fitxer, busca on hi ha la informació del paquet "flashplugin-nonfree". A la línia en concret que estem buscant, t'hauria d'aparèixer com a "Package: flashplugin-nonfree". Esborra des d'aquesta línia fins a la següent que comenci amb "Package: " (no inclosa).

Després d'això, fes un "sudo apt-get install flashlpugin-installer" per tal que t'instal·li el paquet de flash.

---

### Post by trinkus on 2010-03-11
Genial!

Era exactament com deies! Moltissimes gràcies!

---

### Post by marchur on 2010-03-12
Exacte, just la setmana passada em passava a mi això, i l'Oriol m'ho va solventar (com tantes altres coses).

Sort en tenim dels que en saben! :)

Salut!

---

