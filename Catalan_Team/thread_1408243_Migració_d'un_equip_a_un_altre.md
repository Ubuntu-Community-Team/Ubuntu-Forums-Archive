---
title: "Migració d'un equip a un altre"
date: 2010-02-16
forum: Catalan Team
---

### Post by ximoberna on 2010-02-16
Aquest cap de setmana he trobat un Dell Inspiron baratet i he intentat posar-li Ubuntu i migrar el meu perfil d'un altre PC ja instal·lat. 
He intentat la instal·lació des del mateix live-cd que vaig fer-ho en aquell amb la Karmic.

M'he trobat amb les limitacions (o bé no m'apanyat, potser siga això) per a trobar una altra alternativa que acceptar la suggerència d'empetitir la partició del vistaNoVista sense tocar la partició per a backup que venia amb l'equip. De manera que no he pogut fer el que sí que m'ha deixat fer alguna altra instal·lació sobre zero amb una altra distro ben és cert... Empetitir la NTFS fins a crear un espai en blanc prou gran per configurar les particions com a mi m'agrada i, per descomptat, deixar la /home en una a banda...

M'he trobat amb un particionador un poc enrevessat per això i al final s'ha quedat tot l'espai per a una gran Ubuntu ext4 amb tot i una de petita per a swap. Total, que hauré de fer una instal·lació nova amb còpia de seguritat de tot de nou posterior a la supressió d'aquesta i la reconfiguració de la taula de partcions a ma... 
No sé si es podria fer sobre la marxa un escurçament de la ext4 per arribar-hi, és la primera volta que estic tractant amb aquest tipus de fs.

Salutacions

---

### Post by ximoberna on 2010-02-19
> **ximoberna said:**
> Aquest cap de setmana he trobat un Dell Inspiron baratet i he intentat posar-li Ubuntu i migrar el meu perfil d'un altre PC ja instal·lat. 
He intentat la instal·lació des del mateix live-cd que vaig fer-ho en aquell amb la Karmic.

M'he trobat amb ...(o bé no m'apanyat, potser siga això) per a trobar una altra alternativa que acceptar la suggerència d'empetitir la partició del vistaNoVista sense tocar la partició per a backup que venia amb l'equip. De manera que no he pogut fer el que sí que m'ha deixat fer alguna altra instal·lació sobre zero amb una altra distro ben és cert... Empetitir la NTFS fins a crear un espai en blanc prou gran per configurar les particions com a mi m'agrada i, per descomptat, deixar la /home en una a banda...



Sembla que hauria d'haver-me [llegit el manual abans]("https://help.ubuntu.com/9.10/installation-guide/i386/non-debian-partitioning.html")...  Perdoneu :lolflag: ](*,) 
Em sembla que hauré de fer-lo tot de nou suprimint la partició ext4 i creant-ne de noves per a / i /home etc.
De moment estic provant el Google Earth amb la tarja de 256 megues. Va a tope! glxgears em dóna 8500 FPS o més :D

Salutacions!

---

