---
title: "La lectora de Cd sembla haver-se declarat en vaga. (no monta)"
date: 2011-04-23
forum: Catalan Team
---

### Post by cafedescafeinat on 2011-04-23
Bona nit, 

Després, i ho reconec, d'intentar instal.lar un programa, que encara no he aconseguit fer-lo funcionar, (GDM) he instal.lat també el C++ (o això crec) i  el Build-essencials, ara resulta que la meva lectora no funciona.

He buscar per internet i he provat el següent, però continua sense funcionar. Bé, les respostes de l'ubuntu són una mica esfraidores.

Sabríeu dir-me el per què?

[HTML]cafedescafeinat@cafedescafeinat-OptiPlex-GX270:~$ eject /dev/sr0
(l'ha expulsat)
cafedescafeinat@cafedescafeinat-OptiPlex-GX270:~$ sudo mount /dev/sr0
[sudo] password for cafedescafeinat: 
mount: no s'ha pogut trobar /dev/sr0 a /etc/fstab o /etc/mtab
cafedescafeinat@cafedescafeinat-OptiPlex-GX270:~$ sudo mount /dev/sr0 /media/cdrom
mount: el punt de muntatge /media/cdrom no existeix
cafedescafeinat@cafedescafeinat-OptiPlex-GX270:~$[/HTML]

---

### Post by wgarcia on 2011-04-24
Suposo que poses un disc d'algun tipus (dades, àudio) etc. a la unitat, oi? En principi s'hauria de muntar sol cada cop que poses un disc. Per veure si dóna algun error es pot posar algun disc, i mirar les últimes línies de la comanda "dmesg" des d'una terminal, que dóna informació sobre els missatges del sistema. 

Quan fas l' "eject" el que fa es desmuntar el disc que tenies inserit, i per tant és normal que no estigui muntat si no hi ha cap disc. 

Per un altre cantó el que t'està dient el missatge de la comanda "mount" és que no existeix cap carpeta anomenada /media/cdrom. Tampoc fa falta crear-la per als muntatges normals (es crea el que es diu un "enllaç simbòlic" cada cop que s'insereix un disc).

---

