---
title: "Cable Creuat"
date: 2010-11-12
forum: Catalan Team
---

### Post by tanreb20 on 2010-11-12
Hola amics!

Estic intentant conectar dos ordinador amb ubuntu amb un cable creuat, de tal manera que pugui enviar arxius d'un a l'altre de manera rapida, ja que per wifi es més aviat leeeeeent.

Algu se  li acudeix com? :S

---

### Post by wgarcia on 2010-11-12
Connectes el cable creuat a la connexió de xarxa de les dues màquines. 

Suposant que a les dues la connexió de xarxa està a "eth0" (ho pots confirmar entrant "ifconfig" a una terminal i veient si efectivament eth0 està associat a la connexió de xarxa). 

Vas a la primera, i en una terminal entres:

sudo ifconfig eth0 192.168.1.1 netmask 255.255.255.0 up

(potser hagis d'aturar el network manager primer, 
sudo service network-manager stop)

Després vas a l'altra màquina i entres:

sudo ifconfig eth0 192.168.1.2 netmask 255.255.255.0 up

Si funciona comenta-ho perquè la veritat és que no ho he provat jo mateix.

---

### Post by tanreb20 on 2010-11-12
EI!

Ho provaré, peor m'he donat conte que el meu cable no es creuat i no en tinc cap d'aquesta mena, he d'aconseguir-ne un!

---

### Post by CarlesOriol on 2010-11-14
Si els ordinadors son prou moderns no et caldrà que sigui creuat, ja que ho detecten automàticament.

---

