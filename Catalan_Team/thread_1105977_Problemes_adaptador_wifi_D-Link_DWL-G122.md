---
title: "Problemes adaptador wifi D-Link DWL-G122"
date: 2009-03-25
forum: Catalan Team
---

### Post by pablinsfc on 2009-03-25
Hola companys,

fa dies que tinc problemes amb un adaptador D-Link DWL-G122 (rev C). Tot i que em detecta la xarxa wifi i em permet posar-li la contrassenya, no acaba de connectar. Les dues boles del NetworkManager es posen verdes com si realment sincronitzés amb la xarxa, però al cap d'uns segons em torna a sortir la plana del password. He revisat mil vegades que sigui correcte i no entenc perquè no m'hi deixa accedir.

Us agrairia qualsevol suggeriment de com solventar-ho.

Gràcies per endavant!!

---

### Post by khelben1979 on 2009-03-25
There's a thread here. Look [here]("http://www.linuxquestions.org/questions/linux-wireless-networking-41/d-link-dwl-g122-245602/#post1495906"). Maybe it can help you?

¿Usted entiende inglés?

---

### Post by Diegstroyer on 2009-03-25
No tindràs un filtre de MAC activat? Només et passa a casa teva? Ho has provat en un altre lloc?

Salutacions.

---

### Post by pablinsfc on 2009-03-25
@khelben1979: Thank you, but in this link, it seems that they have not solutions for this problem!

@Diegstroyer: No el tinc pas activat, amb el guindous funciona :(

---

### Post by Diegstroyer on 2009-03-26
Et pots connectar a altres xarxes?

---

### Post by Aeryal on 2009-03-27
Ei gent, a mi em passa el mateix, i jo he provat de connectarme a altres xarxes i en algunes puc i en d'altres no. 

PD: Jo faig servir una tarjeta wireless diferent al meu ordinador.

---

### Post by SiscoGarcia on 2009-03-27
> **Aeryal said:**
> Jo faig servir una tarjeta wireless diferent al meu ordinador.

Llavors potser millor que obris un altre fil perquè la solució pot ser diferent.

PD: Recorda de revisar el [fil d'iniciació]("http://ubuntuforums.org/showthread.php?t=599965").

---

### Post by oriolsbd on 2009-03-27
Hola. Alguns cops, en aquests mateixos fòrums, quan hi ha hagut problemes amb el Network Manager s'ha recomanat el gestor de xarxes Wicd. Si la xarxa funciona amb el Network Manager, a mi m'agrada més que el Wicd. Però és cert que hi ha casos en què el Network Manager no va bé, i el Wicd sí. El podeu provar.

[Aquí]("http://wicd.sourceforge.net/download.php") teniu instruccions sobre com configurar els seus repositoris per a instal·lar-lo (aneu a la secció "Installing Wicd in Ubuntu" i seguiu les instruccions canviant "hardy" per "intrepid" si esteu utilitzant Ubuntu 8.10).

Per cert, quan intenteu instal·lar el Wicd us desinstal·larà el Network Manager. És correcte, no us espanteu. :-)

---

### Post by oriolsbd on 2009-03-27
Per cert, hi acabo de pensar. Com s'ho instal·laran, encara que sigui a través de repositoris, si no tenen xarxa? És divendres, de nit, i el meu cervell ja no dóna per més, aquesta setamana... :-)

La millor manera, si és possible, és connectar-vos al router per cable, i així instal·lar el Wicd amb els repositoris configurats com us he passat abans. Després, si tot va bé, ja us hi podreu connectar per Wifi.

L'altra manera, és baixar-vos des d'un altre ordinador el fitxer .deb del Wicd del Sourceforge. El podeu trobar [aquí]("http://sourceforge.net/project/showfiles.php?group_id=194573&package_id=229460&release_id=659059"). El passeu a l'ordinador on vulgueu instal·lar el Wicd, i executeu des d'un terminal:
```
sudo dpkg -i wicd_1.5.9_all.deb
```

Salut! :-)

---

### Post by pablinsfc on 2009-04-05
Gràcies oriolsbd, ho provo i us dic el què. Del que comentaves del cable... és més aviat difícil connectar al router així. Provaré descarregant els .deb.

Moltes gràcies!

Pau.

---

### Post by quitus on 2009-04-06
jo mai vaig poder connectar-me a una xarxa amb una "potencia" inferior a 60 no se si serà pas el teu cas.

salut

---

### Post by Molsa on 2009-04-10
Jo estic exactament com tu, amb el mateix wifi. Però no he sabut conectar-me directament amb el cable, tampoc.

---

### Post by pablinsfc on 2009-04-13
Ja està! Finalment ho he aconseguit nois! He descarregat el paquet com deieu i funciona. Crec que no faré servir més el NetworkManager! :s

Moltes gràcies a tots per l'ajuda!

A reveure!

Edito: No trobo la opció o tag per marcar el fil com a resolt... que no hi és ja?

Edito2: Per cert, moltes felicitats pel nou disseny de la plana, està molt bé i m'agrada més que l'anterior! :)

---

