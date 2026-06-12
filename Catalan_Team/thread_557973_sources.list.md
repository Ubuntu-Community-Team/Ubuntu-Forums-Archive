---
title: "sources.list"
date: 2007-09-23
forum: Catalan Team
---

### Post by prostata on 2007-09-23
Haig de toquinejar aquest fixer i necessito permisos de lectura escriptura i tot, malgrat que amb el botó dret del ratolí ho he intentat no puc donar-li permisos. Com puc fer-lo???. Em sorpren una mica la subtil diferència gràfica entre Kubuntu i Ubuntu, però també la operativa, ja posats a demanar...a Kubuntu com es treuen del menu d'inici ¿? les aplicacions, per exemple:

Inici ¿?
Multimedia
Mplayer XXXXXX

No hi ha una forma gràfica com a Ubuntu, de veure tot lo que arrenca en cada sessió?

---

### Post by prostata on 2007-09-23
He probat amb chmod, que és la comanda més adient, però com que la meva experiència no és molta no me en surto. Ho faig d'aquesta forma;

sudo chmod /etc/apt/sources.list

i evidentment em diu que nones, el ting gaire bé las dits però no,,,,no...., bufff!! em falta algo petit però no sé ben bé.....

---

### Post by papapep on 2007-09-23
Ni se t'acudeixi canviar-li els permisos al sources.list!!!

Símplement fes a un terminal:

```
sudo nano /etc/apt/sources.list
```

Edites el que et calgui, i prems Control+X per a desar els canvis.

PD T'aconsello fer-ne una còpia **prèviament** per a evitar desgràcies.
```
cp /etc/apt/sources.list /etc/apt/sources.list.backup
```

---

### Post by orestesmas on 2007-09-25
No has de canviar els permisos, com diu el papapep. Només has d'invocar un editor amb permisos de superusuari. llavors podràs editar qualsevol fitxer del disc.

Quant a l'edició del menú del KDE (suposo que et refereixes a això) no hi hauria res més fàcil si els senyors d'ubuntu no haquéssin amagat l'editor del menú per no ferir les sensibilitats de les persones susceptibles. Simplement prem Alt+F2 (això és per invocar programes pel seu nom sense necessitat d'obrir una consola) i introdueix allí l'ordre "kmenuedit". El programa és autoexplicatiu, però si vols un cop de mà torna a preguntar.

Vagi bé.

---

### Post by Ferri on 2007-09-25
Si prefereixes editar sources.list en mode gràfic, alt+F2 i:
```
kdesu kedit /etc/apt/sources.list
```
Per editar el menú, també pots fer clic dret al damunt i et surt l'opció.

---

