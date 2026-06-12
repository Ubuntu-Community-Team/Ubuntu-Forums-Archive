---
title: "Clonar Disc Dur"
date: 2009-11-16
forum: Catalan Team
---

### Post by jdk9 on 2009-11-16
Bones de nou!

M'agradaria fer el següent: Tinc a l'ordinador de la següent forma: sda1, amb Windows 7 i sda2 amb Ubuntu (i una tercera partició amb swap). El fet és que vull carregar-me el Windows 7, i en el seu lloc (és a dir, a l'inici del disc dur) posar-hi ubuntu, però em fa molta mandra reinstalar i reconfigurar Ubuntu. Com m'ho puc fer per moure la partició d'Ubuntu (o clonar-la) al principi del disc dur?

Gràcies per avançat!

---

### Post by papapep on 2009-11-16
Suposant que sda1 sigui, com a mínim, tan gran com sda2, i des d'un CD o pendrive en una sessió en viu:

```
sudo dd if=/dev/sda2 of=/dev/sda1
```

això et clonarà bit a bit el disc. No és especialment ràpid, però funcionarà.

Una altra, potser millor, opció, és fer servir el CD viu [clonezilla]("http://sourceforge.net/projects/clonezilla/files/clonezilla_live_alternative/clonezilla-live-20091113-karmic.iso/download"), que et permet clonar discs, particions, etc, des d'un menú una mica més "amigable". En qualsevol cas, està clar que s'imposa una còpia de seguretat de totes les dades importants abans de fer res...
Per cert, tingues present que després hauràs d'arreglar el grub a fi de que t'arrenqui correctament.

---

### Post by X-Tornado on 2009-11-16
Tambe cal recordar que al dd se li pot afegir  la opcio: 
>  -bs=BYTES        lee y escribe la cantidad BYTES de bytes por vez (ver ibs=,obs=)
 Segons la velocidad del disc per acelerar el proces.
Exemple: -bs=8192
Segons he llegit la cantitat ha de ser multiple de 2.
Pero baja que no eh fet servir mai el dd y potser m'etivoco pero crec que que serveix per aixo. aquesta opcio


Tambe cal recordar que el dd tambe et copiara el bits en blanc.

---

### Post by jdk9 on 2009-11-16
He provat el metode amb el CloneZilla. Ha anat ràpid i bé.

A continuació he reiniciat Ubuntu, a la partició 2 i li he fet un sudo update-grub. I no em reconeix la partició sda1, on hi ha el nou Ubuntu :S

Ara estic provant amb el dd a veure que tal va!

Amb el dd em trobo amb el mateix, no m'inicia desde la primera partició, tot i forçar-lo (és a dir, al menu de Grub apretar e i canviant-li la entrada hda(0,1) per hda(0,0). Per cert i per canviar l'swap?

Ara s'em a ocorregut una nova cosa. Podria crear un CD/DVD que es generés amb una còpia de tota la configuració que tinc actualment? Existeix algun programa que ho faci de forma automàtica?

Gràcies

---

