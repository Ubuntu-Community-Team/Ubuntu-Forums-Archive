---
title: "No em detecta la partició després d'un problema amb el maquinari"
date: 2009-11-18
forum: Catalan Team
---

### Post by kukat on 2009-11-18
Pensava que tenia un problema amb el disc dur, però resulta que és el connector IDE. Al canviar-lo per un altre, ja no em tira errades, i em detecata (i esta plenament operativa) la partició /home...

Vaig fer el HDD Regenerator, que em tirava errades a dojo, i ara ja no em tira cap mena d'errada. El que passa es que crec que es van fotre alguns sectors del principi de la partició, i al recuperar-los el HDD regenerator, ja no detecta la partició...o veges tu a saber! :D

Tinc dues particions en el mateix disc dur: una amb el sistema base, i altra amb el /home.  

La que no em detecta es la del sistema base (d'uns 20 a 30 gb). El "gparted" del Karmic Koala CD VIU, em diu que no detecta el sistema de fitxers i aquest surt en negre. 

Al fer un "**mount /dev/sdb1 /mnt -t ext4**" em surt el següent error:

"wrong fs type, bad option, bad superblock on /dev/sdb1"....

Al fer un dmesg | grep /dev/sdb, em sortia la partició del /dev/sdb1 i m'informava del mateix error (No troba el sistema de fitxers que gasta...)

[http://img193.imageshack.us/img193/4076/nohihaext4.png](http://img193.imageshack.us/img193/4076/nohihaext4.png)

[http://img42.imageshack.us/img42/8871/unknownw.png](http://img42.imageshack.us/img42/8871/unknownw.png)

Quan intenta arrancar, es queda en una pantalla, que a sota es veu un "Grub" , però es queda ahí...

He vist ferramentes com "TestDisk", però clar....estic en ext4 i no estic segur de que és el que tinc que fer!!!

La solució senzilla és tornar a instal.lar el sistema base...però solament tinc Internet ací a l'institut!!! A Casa encara tardarà un poc a estar en marxa! :(

Salut!!!

---

### Post by papapep on 2009-11-18
Doncs ho tens complicat, crec. No tinc la més lleugera idea de què fa l'eina aquesta que esmentes, jo hauria tirat per emprar les eines[1] que els fabricants de discs proporcionen per verificar els discs
Pel que sembla, el programa aquest ha liquidat els descriptors del principi del sistema de fitxers.

Tal i com esmentes, [Testdisk]("http://www.cgsecurity.org/wiki/TestDisk") és una de les opcions que tens, però no tinc gaire clar que funcioni com cal amb un sistema de fitxers ext4. Si vols jugar, prova-ho, però planteja't reinstal·lar, i ves amb compte amb aquest disc dur. Jo aprofitaria per passar-li l'eina que pertoqui del fabricant, i fer-li verificacions exhaustives, abans de tornar-hi a posar dades.


[1] Eines d'alguns fabricants:
Seagate/Maxtor: [http://www.seagate.com/www/en-us/support/downloads/](http://www.seagate.com/www/en-us/support/downloads/)
Hitachi: [http://www.hitachigst.com/hdd/support/download.htm](http://www.hitachigst.com/hdd/support/download.htm)
Western Digital: [http://support.wdc.com/product/download.asp?wdc_lang=sp](http://support.wdc.com/product/download.asp?wdc_lang=sp)

---

### Post by kukat on 2009-11-19
Gràcies! Doncs tampoc passa res, perquè tinc el /home separat, però el problema és que no tinc internet a casa de moment. Però bé...tampoc passa res...
Li pegaré una ullada a les ferramentes de Maxtor (és un Maxtor). De moment el HDD Regenerator no li va tirar errors, però la veritat es que el disc dur aquest és un poc problemàtic!!!

Salut!

---

