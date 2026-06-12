---
title: "Actualització de controladors automàtica"
date: 2011-08-25
forum: Catalan Team
---

### Post by Frealof on 2011-08-25
Molt bones, 

Fa temps em vaig comprar un adaptador PCI per a connectar-me a una xarxa sense fils ( Network controller: RaLink Device 3062). Resulta que, pel què sigui, Ubuntu no el té a la llista i cada vegada que actualitzo sistema em trobo que haig d'anar a la carpeta on tinc els controladors de la targeta i tornar-los a carregar manualment (make , make install, modprobe...). Hi hauria alguna manera, de fer/escriure/crear una ordre perquè això es fes de manera automàtica?

Gràcies.

---

### Post by kimet on 2011-08-25
Es possible que et carregui mòduls equivocats.
Una possible sol.lució es posar en llista negra els moduls que no funcionen, busca amb lsmod els que comencen per 'rt' i els poses a /etc/modprobe.d/blacklist.conf.
I després posar a /etc/modules el modul correcte.

Si de cas no t'en surts posa la sortida de lsmod.

---

### Post by snoopo71 on 2011-08-25
> **Frealof said:**
> Molt bones, 

Fa temps em vaig comprar un adaptador PCI per a connectar-me a una xarxa sense fils ( Network controller: RaLink Device 3062). Resulta que, pel què sigui, Ubuntu no el té a la llista i cada vegada que actualitzo sistema em trobo que haig d'anar a la carpeta on tinc els controladors de la targeta i tornar-los a carregar manualment (make , make install, modprobe...). Hi hauria alguna manera, de fer/escriure/crear una ordre perquè això es fes de manera automàtica?

Gràcies.

Pots fer un petit script en [Bash]("http://tldp.org/LDP/Bash-Beginners-Guide/html/") amb les ordres que executes a la consola i executar-lo cada cop que actualitzis.

---

