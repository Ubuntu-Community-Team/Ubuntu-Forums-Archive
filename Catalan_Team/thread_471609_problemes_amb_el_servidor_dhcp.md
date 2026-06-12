---
title: "problemes amb el servidor dhcp"
date: 2007-06-12
forum: Catalan Team
---

### Post by bratac on 2007-06-12
Bones, 

a la feina tinc un router inalàmbric a través del qual fins fa poc m'havia connectat amb el meu ordinador personal (amb ubuntu) Aquesta setmana ha canviat el tipus de connexió i no puc connectar-me a l'internet, però sí a a la wifii.

He mirat els paràmetres de la connexió i són els següents en windows (tots els ordinadors amb windows es connecten sense cap problema)

Dirección física: 00-16-6F-71-3B-4C
Dirección IP: 192.168.1.35
Máscara de subred: 255.255.255.0
Puerta de enlace predeterminada: 192.168.1.1
Servidor de DHCP: 192.168.1.1
Concesión obtenida: 12/06/2007 12:51:41
La concesión caduca: 13/06/2007 12:51:41
Servidores DNS: 80.58.61.250, 80.58.61.254
Servidor WINS: 

amb ubuntu tinc:

ip 192,168.1.57
Adreça de multidifusió: 192.168.1.255
Màscara de subxarxa: 25.255.255.0
Ruta predeterminada: 192.168.1.1
i les dns són iguals que a windows.

Per comparació veig que el problema rau en l'adreça de multidifiusió, no? Com ho puc fer per arreglar-ho?

fins ara, 

alfred

---

### Post by patrickfromspain on 2007-06-12
Podries probar a posar la conexio per a que agafes la direccio automaticament, a veure que pasa.

salut!

per cert, abans de res, probar a fer un sudo /etc/init.d/networking restart a veure si va

---

### Post by bratac on 2007-06-12
ja ho he provat, tant de posar la dhcp automàtica, com de configurar manual la connexió però em dóna error (deu ser per que el servidor reparteix les ip automàticament)

fins ara,

---

### Post by patrickfromspain on 2007-06-12
be, si ens dius quin hardware tens, quin error et dona i tot aixo, potse et podrem ajudar ;)

---

### Post by bratac on 2007-06-14
Solet, no sé com ni per que se m'ha acabat connectant (misteris de la tècnica)

gràcies a tots

Alfred

---

