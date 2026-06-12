---
title: "Amagar sda1"
date: 2007-04-26
forum: Catalan Team
---

### Post by boriffus on 2007-04-26
Bon dia.
Porta ja 3 dies amb el nou ubuntu feisty fawn i encara he estat incapaç de fer una cosa que amb l' Edgy no recordo que em costés tant: 
resulta que no sé on vaig trobar unes instruccions que permetien amagar la partició d' un windows que tinc al disc dur i que sempre apareix a l' escriptori del feisty. 
Si no recordo malament, es tractava d' un arxiu de comandes que s' autoexecutava a l' iniciar el sistema (crec que des de d' alguna carpeta del /root), però el cas és que no ho recordo exactament i no acabo de trobar la pàgina on ho vaig veure. 
Sí que puc fer un umount però el sistema segueix veient que hi ha una partició i permet muntar-la, i el que vull és que ni es vegi ni es permeti muntar-la ni res, com si no existís.
Algú de vosaltres ho ha fet o sap com es fa...? O on puc trobar instruccions?

Gràcies!

---

### Post by patrickfromspain on 2007-04-26
gksudo gedit /etc/fstab i comentes la linea que fa referencia a sda1

---

### Post by boriffus on 2007-04-27
Gràcies per la resposta, però si faig això, és cert que a l' iniciar ubuntu ja no m' apareix sda1 a l' escriptori, però en el nautilus m' apareix una partició com a desconeguda o algo així, i no només això, sinó que permet muntar-la i fer-la servir. 
El que vaig fer amb l' edgy feia que desaparegués completament, mira que he remirat i no ho acabo de trobar... l' únic que recordo és que posava un arxiu que s' autoexecutava des d' una carpeta de root, però no recordo quines comandes es posaven en aquest arxiu.... 
En fi, seguirem buscant.

Gràcies de totes maneres!
boriffus

---

### Post by lluisanunez on 2007-04-27
Crec que Nautilus mira sempre el que hi ha sota "media". Si muntes la partició en un altre lloc, com /mnt, em sembla que ja no t'apareixerà, encara que hi podràs accedir sempre desde /mnt.

```
sudo mkdir /mnt/sda1
sudo chown [username] /mnt/sda1
sudo chgrp [username] /mnt/sda1
sudo mount -a
```

Respecte a això de recordar les paraules màgiques que has usat per arreglar les coses, hi ha una eina fantàstica per anotar-les a Ubuntu que és TomBoy (s'instal·la com un applet del panel) i és com entre Post-it i wiki personal. El recomano molt

---

