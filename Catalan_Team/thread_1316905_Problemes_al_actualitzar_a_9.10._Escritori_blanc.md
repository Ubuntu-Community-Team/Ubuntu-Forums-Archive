---
title: "Problemes al actualitzar a 9.10. Escritori blanc"
date: 2009-11-06
forum: Catalan Team
---

### Post by pserra on 2009-11-06
Hola, 
l'altre dia vaig voler actualitzar el sistema i per variar..
he quedat encallat al arrencar tinc:
-el gnome em surt la cersio 9.4...
- al carregar em carrega l'interfície nova... m'agrada.. els anegrames blans estan bé... diferents..
- al carregar ja em surt algun error però la finestra s'obre i tanca molt ràpit
- al cap de 1 minut(més o menys )  quan sembla que el sistema esta carregat i llavors la pantalla es posa negra unes dècimes  per carregar l'escriptori... se'm queda la pantalla blanca..

que he fet?
vaig a recovery mode i si vull recòrrer el llistat avall se'm bloqueja tot i em sobreposen els missatges:

Mountall cancelled
General error mounting filesistems
A maintenance shell will now be started
CONTROL -D will terminate this shell and retry
Give rrot passsword for maintenance
or typer control -D to continue

si li dono tab vaig a la consola i faig els
   sudo aptitude update
   sudo aptitude full-upgrade
però no actualitza rés...

que puc fer??
Merci

---

### Post by pserra on 2009-11-07
alguna suggerencia?  
Merci

---

### Post by pserra on 2009-11-08
Hola, ja ho he solucionat.... he trobat la solució en un altre llloc..
per si algú li passa, pot fer:
$  sudo  uname -r  (per conèixer el nucli, em donava 2.6.28.13)

he fet:
$   sudo  mv  /boot/grub/menu.lst /boot/grub/menu.lst.copia
$   sudo   update-grub
$   sudo   reboot
 i ja està....
ara em surt  de nucli: 2.6.31-14-generic


A reveure...

---

