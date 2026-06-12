---
title: "Recuperar dades de disc dur USB"
date: 2011-03-10
forum: Catalan Team
---

### Post by Curial on 2011-03-10
No se si algú em pot ajudar amb un error força greu, que he comés intentant fer una imatge d'una partició.

La meva intenció era generar un arxiu (imatge) en un disc dur de 250Gb extern d'una partició de 100Mb d'un disc dur intern.

La comanda que he teclejat des del terminal per error ha estat:

sudo dd if=/dev/sd4 of=/dev/sdc bs=1M

Això m'ha convertit el disc sencer com si només tingués el contingut de la partició sd4.

No se si encara tinc alguna possibilitat de recuperar la informació original del disc extern.

Gràcies.

---

### Post by kimet on 2011-03-10
He recuperat particions senceres amb testdisk, eran particions formatejades per error, en el cas d'haver escrit a sobre no se si et funcionarà al 100%.
[http://www.cgsecurity.org/wiki/TestDisk_Paso_A_Paso](http://www.cgsecurity.org/wiki/TestDisk_Paso_A_Paso)
De totes maneres, si tens la possibilitat de treballar sobre una còpia tindràs mes d'una oportunitat.
També existeix PhotoRec, que no he fet servir mai...

Salut

---

### Post by wgarcia on 2011-03-11
Depenent de la grandària del disc que estaves copiant podran quedar dades sense esborrar o no. La comanda "dd" és justament per sobreescriure el disc de destí, cosa que no es fa quan simplement esborres un fitxer o canvies les particions, fins que no escriguis les dades encara hi són al disc. 

Per si hagués quedat alguna cosa al fil següent es discuteixen diversos mètodes per recuperar dades:

[http://ubuntuforums.org/showthread.php?t=1471031](http://ubuntuforums.org/showthread.php?t=1471031)

---

### Post by Funk'u on 2011-03-12
He utilitzat el TestDisk, i he recuperat tot i més, el Photorec forma part del TestDisk, ossigui que si l'instal·les ja l'hi tindràs, és força intuitiu, el problema que hi veig és que et fa un munt de carpetes amb un munt d'arxius dins que has d'anar obrint i canviant el nom i classificant, i és feina de xinos la veritat.




Salut!

---

### Post by wgarcia on 2011-03-13
Les dades hi són, però s'ha perdut la referència que utilitza el sistema operatiu per saber on són al disc i com te les ha de mostrar. Però tingues en compte que hi ha empreses que es dediquen a recuperar discos i fan exactament el que has fet tu.

---

### Post by kukat on 2011-03-14
A mi el Photorec no m'ha fallat mai. 

A la meua web hi ha un tuto de com el faig servir:

[http://www.jordijuan.com/informatica/recuperacio-de-dadesfotos-documents-etcetera-mitjancant-photorec-i-gnulinux](http://www.jordijuan.com/informatica/recuperacio-de-dadesfotos-documents-etcetera-mitjancant-photorec-i-gnulinux)


Salut!

---

