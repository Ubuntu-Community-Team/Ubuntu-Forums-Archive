---
title: "Treure windows"
date: 2020-02-04
forum: Catalan Team
---

### Post by rvprada on 2020-02-04
Hola, havia tingut una molt bona experiència amb ubuntu amb un ordinador que vaig comprar sense windows. Després en comprar un altre que tenia windows vaig decidir instal·lar ubuntu respectant una partició per windows per si m'anava bé per algo. Ara, després d'un any en el que no he obert windows ni una sola vegada crec que el millor que podria fer seria treure'l del tot perquè ocupa un espai sense fer cap servei. I no tinc ni idea com fer-ho, hi ha algun lloc on s'expliqui? És molt complicat?
Moltes gràcies per endavant.

---

### Post by wgarcia on 2020-02-06
No és complicat, es tracta d'eliminar la partició que conté Windows. L'únic complicat és que convé fer-lo sense tenir muntat el disc que conté les particions d'Ubuntu i Windows, per tant et cal un USB d'instal·lació de l'Ubuntu. El procediment seria el següent:

1) Primer convé fer còpia de les dades que tinguis al Windows, però jo també en faria de les que tens a l'Ubuntu per si un cas, sempre convé tenir còpies de seguretat de tot per si hi ha algun problema.

2) Suposant que tens un USB o disc d'instal·lació de l'Ubuntu, inicies l'ordinador amb aquest dispositiu, i esculls "Tria l'Ubuntu" (no "Instal·la l'Ubuntu").

3) Un cop s'inicia l'Ubuntu de prova, obres una aplicació que es diu GParted.

4) Selecciones la teva partició de Windows (serà de tipus NTFS i probablement tindrà una vora verda clara), i esculls Partició -> Eliminar.

5) Et quedarà un espai al disc sense utilitzar per cap partició, per tant convé incrementar la mida de la partició d'Ubuntu per aprofitar aquest espai. Veuràs que el Gparted té opcions per canviar de mida les particions, ho pots fer gràficament arrossegant el límit de la partició on tens l'Ubuntu.

6) Tanques el Gparted i reinicies el sistema ara des del teu disc dur. Un cop que estàs a l'Ubuntu un altre cop, obres una terminal i entres 

```
sudo update-grub
```

Això treurà el Windows del menú d'inici. De fet si sols et queda l'Ubuntu, potser en iniciar l'ordinador arrenqui directament l'Ubuntu sense mostrar-te el menú inicial com quan tenies Windows.

---

### Post by bielfiol on 2020-04-11
Tenc un cas similar. Vaig instal·lar la 19.10 junt amb Windows i vaig reservar menys espai que al Windows.
Jo no vull eliminar Windows però sí reduir la seva partició i ampliar la de Linux. Això implicaría mouré l'inici de la partició d'arrencada de Linux. 
Si seguesc les mateixes passes, substituint eliminar la partició windows per redimensionar-la, es mantindria el "dual boot"?
El meu dubte és realment si l'"update-grub" sería suficient ho hauria de fer més canvis.
M'he oblidat de comentar que tenc el sistema amb UEFI.

---

### Post by wgarcia on 2020-04-12
Per veure exactament què s'ha de fer, seria convenient veure amb detall quina és la disposició de les particions. Però per això millor obrir un altre fil amb el tema específic del teu cas. Obres un terminal i entres:

```
sudo fdisk -l
```

Copies i enganxes el resultat a [https://paste.ubuntu.com/]("https://paste.ubuntu.com/") i enganxes al missatge l'enllaç a això.

---

### Post by rvprada on 2020-06-12
Wgarcia, escric només per disculpar-me per no haver contestat, s'han passat els dies sense fer-ho i al final han estat mesos, gràcies per tot. Al final vaig tenir un problema amb l'ordinador que no arrencava i vaig haver d'instal·lar ubuntu des del principi i ja ho vaig fer sense windows, fent servir un usb d'instal·lació per salvar les dades. Moltes gràcies per la feina que feu.

---

