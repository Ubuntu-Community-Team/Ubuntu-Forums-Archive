---
title: "La instal·lació de ubuntu no reconeix les unitats ni particions"
date: 2009-11-13
forum: Catalan Team
---

### Post by ArcA on 2009-11-13
Doncs aquest és el problema, al intentar instal·lar ubuntu, ja sigui la 9.10, la 8.04. El problema resideix en que tot funciona ok, excepte quan estic al pas de les particions, que tot em surt en blanc, no em dona opció a res. He utilitzat el gparted, ja que desde la live puc treballar, però no es veu res, ni la partició de win ni on tinc el 7.04.

He rebuscat sobre aquest tema a diversos llocs, i, he pensat que deu de ser pels hdd que són sata, i la gent deia q entrés a la bios i els hi canvies per ide, doncs ho he fet i res. Continua igual.

Algú te alguna idea?

Gràcies.

---

### Post by papapep on 2009-11-13
Prova passant-li el paràmetre "noraid" a l'arrencada. He vist casos en què el sistema pensa que diversos discos SATA són una matriu de discos en RAID, encara que no ho siguin.

---

### Post by ArcA on 2009-11-13
ok, el que he fet. Clar està abans de veure que m'havies contestat.
He entrat a la bios i ho he posat com a ata. M'ha petat tot.
Em deia que com tinc dos hdd enchufats en sata, que no ho reconeixia, que en tragues un. Doncs així ho he fet.
Total que ara he entrat com ata a la bios, ara sembla com si fos ide, i el gparted em reconeix les particions de windows, que tenia en aquest hdd.

Papa, aixo confirma el que deies?

Gracies ara ho provo.

---

### Post by papapep on 2009-11-13
> Papa[COLOR="Red"]pep[/COLOR], aixo confirma el que deies?

Jo diria que sí.

---

### Post by ArcA on 2009-11-23
doncs ho he provat i no em funciona això que dius papapep. 
He reiniciat el pc, li he donat a f6 lo de altres opcions i com no hi era li he afegit al final. Però res de res. El problema quin és ara?
Doncs que vaig veure que tenia un instalador per a windows. Doncs vaig pensar, doncs peto la particio de linux amb el partition magic, la formatejo a ntfs, i desde win instalo ubuntu a aquesta particio nova, que win si q me la reconeix. Problema, he petat el grub, ara no em carrega res :popcorn: 
Clar, poso la live per fer fdisk /mbr, però com no reconeix els hdd pq son SATA doncs no pot trobar la MBR.

Ains, que puc fer?
a plorar a on...¿?
ja ja ja 
Gràcies de nou...

---

