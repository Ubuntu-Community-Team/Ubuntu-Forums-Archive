---
title: "Wicd i Xarxa oculta amb WPA2 &amp; MAC"
date: 2011-02-17
forum: Catalan Team
---

### Post by JUSTERINI1 on 2011-02-17
Hola!
Fa poc he instal.lat el Wicd i ja vàrem començar amb el peu esquerre perquè no em connectava al router. Finalment he descobert que si tinc la xarxa visible em connecta sense problemes, però si la poso oculta, automàticament ja perdo la connexió i no hi ha manera, em diu que o bé tinc el password mal.lament (no és veritat) o es connecta al router però no m'assigna IP, ho he provat del dret i del revés, fins i tot vaig actualitzar al ubuntú 10.04 (no se com es diu, és que els hi poseu uns noms molt raros i difícils) per si hi tenia res a veure, però res, continua igual si oculto, no connecto.
La encriptació és WPA2 amb adreces MAC.
Alguna idea? 
#-o
Gràcies per endavant.

Justerini

---

### Post by kimet on 2011-02-17
A mi si em conecta.
Si cliques al botó de l'esquerra on diu xarxa > "find a hidden network", no es conecta?
Per altra banda no serveix de gaire res...

Salut.

---

### Post by JUSTERINI1 on 2011-02-17
Hola
Si clico al find hidden network, troba la xarxa però no es connecta (la troba però sense indicar-ne el nom, per exemple, li dic que busqui la xarxa "xarxa" i em troba una adreça tipus 0000,0000,0000etc 
Ja se que no serveix de gaire la ocultació, però si més no és una xarxa menys de la llarga llista del veïnat.
Crec que ha de ser un problema de configuració, perquè amb un netbook el Wicd (ve amb el Jolicloud) se'm connecta sense problemes.

---

### Post by pelai21 on 2011-02-20
Jo tenia un problema similar. Quan ocultava la xarxa o tractava d'afegir-hi un filtre MAC no em podia connectar des l'Ubuntu -i no només amb el Wicd, sinó també amb Network Manager-. Al final vaig decidir posar-hi una clau WPA ben llarga, i de tant en tant reviso la xarxa amb l'nmap. Si trobes una solució, ja ens ho diràs. Vés a saber si no hi ha alguna mena d'incompatibilitat amb el router...

---

