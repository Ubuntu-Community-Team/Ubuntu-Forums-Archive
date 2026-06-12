---
title: "Empathy"
date: 2010-11-18
forum: Catalan Team
---

### Post by tanreb20 on 2010-11-18
Hola!

Fa un parell de dies actualitzant PPA's etc... em va passar uan cosa extranya, abans quan conectava l'empathy es quedava "minimitzat / en segon pla" i en el indicator-menu sortia una flecheta a l'apartat "CHAT", aquesta ara no surt i m'obliga a tenir l'empathy en "semiprimerpla", adjunto un parell de fotos, a veure si algú ho enten.

[IMG]http://img269.imageshack.us/img269/4609/men003.jpg[/IMG]

[IMG]http://img600.imageshack.us/img600/1717/seleccin001g.jpg[/IMG]

Perdoneu per la qualitat de les fotos, no se xq el shutter ha decidit fer el burro!

---

### Post by kukat on 2010-11-18
edito : m'he equivocat

---

### Post by tanreb20 on 2010-11-19
eing?

---

### Post by wgarcia on 2010-11-20
Fas servir l'escriptori Gnome o el KDE? En cas facis servir Gnome, has remogut l'evolution? A vegades aquestes coses estranyes amb els indicadors passen quan es remou l'evolution, perquè està molt integrat amb l'escriptori i tot que no es faci servir convé no remoure'l.

---

### Post by tanreb20 on 2010-11-20
Efectivament faig servir el GNOME pero amb l'evolution intacte, ja qeu l'utilitzo com a gestor de correu (dec ser dels pocs...)

---

### Post by wgarcia on 2010-11-20
Un altre suggeriment és canviar-li el nom a la carpeta ".gnome2" que tens al teu home i reiniciar l'escriptori, i veure si s'arregla.

Obrint una terminal, des del teu "home" estant:
mv .gnome2 .gnome2.antic

per exemple.

En reiniciar l'escriptori el sistema tornarà a crear aquesta carpeta amb el nom ".gnome2". 

Si no s'arregla pots esborrar la nova ".gnome2" i tornar a anomenar la carpeta que havies canviat de nom a ".gnome2":

rm .gnome2
mv .gnome2.antic .gnome2

---

### Post by tanreb20 on 2010-11-20
Bé ja s'ha solucionat.

No sé exactament perque pero el empathy no em funcionava.

He fet un sudo dpkg --configure -a (l'havia oblidat aquesta comanda) i ja funciona amb absoluta normalitat!

---

