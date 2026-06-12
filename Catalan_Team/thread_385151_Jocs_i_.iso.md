---
title: "Jocs i .iso"
date: 2007-03-15
forum: Catalan Team
---

### Post by Joanrcp on 2007-03-15
M'he descarregat amb el bittorrent un joc i m'han baixat tres arxius .iso
Voldria ejecutar-los amb el wine, però... com ho faig? 
Cal fer alguna cosa amb els .iso abans?

---

### Post by orestesmas on 2007-03-15
Els .iso són imatges de CD comprimides. pots fer 2 coses:

1) Gravar la imatge en un CD i llavors ja podràs accedir als continguts i fer-ne el que vulguis.

2) Muntar la imatge amb l'opció "loop", que et permetrà fer el mateix que 1). això es fa amb:
sudo mount -t iso9660 -o loop fitxer.iso punt_de_muntatge

on "punt_de_muntatge" és un directori buit qualsevol. Llavors pots accedir a aquest directori com si fossin els continguts del CD.

Em sona que el wine té una opció per fer quelcom semblant a 2), però veure-ho directament des de windows. No conec massa el wine, hauràs d'investigar tu mateix.

---

### Post by Joanrcp on 2007-03-15
merci però em dóna aquest error:
> 
wrong fs type, bad option, bad superblock on /dev/loop0,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so



Què puc fer ara?

---

### Post by orestesmas on 2007-03-15
Això pot indicar dues coses: que tens la imatge ISO malament (corrupte) o bé que has entrat l'ordre malament.

Si et plau, per anar descartant opcions, pots dir *exactament* quina ordre has entrat?

---

### Post by Joanrcp on 2007-03-15
Sí. 

Primer, m'he situat a la carpeta on tinc l'arxiu .iso (és: AOM_D1.iso) amb:
> cd /home/joanr/Jocs/Age_of_Mythology

Una vegada aquí, executo l'ordre:

> sudo mount -t iso9660 -o loop AOM_D1.iso /Age-of-mythology-joc


On /Age-of-mythology-joc és una carpeta buida que he creat.

I ara el que em surt és:
> mount: El punt de muntatge /Age-of-mythology-joc no existeix


Com ho veus??

---

### Post by orestesmas on 2007-03-15
Doncs que si poses /Age-of-mythology-joc li estàs dient que aquesta carpeta l'has creada al directori arrel, cosa poc probable (ja que ho hauries d'haver fet amb permisos de superusuari).

Posa-li correctament la ruta al directori on vols muntar la imatge. Si és dins el directori actual, treu-li la "/" del davant.

---

### Post by Joanrcp on 2007-03-16
orestesmas,

Ho he probat treient la / 
> 
 sudo mount -t iso9660 -o loop AOM_D1.iso Age-of-mythology-joc


i posant tota la ruta de l'arxiu i

> sudo mount -t iso9660 -o loop AOM_D1.iso /home/joanr/Jocs/Age_of_Mythology/Age-of-mythology-joc


però, la resposta de la terminal és, tant en un cas com en l'altre:

> mount: wrong fs type, bad option, bad superblock on /dev/loop0,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


---

