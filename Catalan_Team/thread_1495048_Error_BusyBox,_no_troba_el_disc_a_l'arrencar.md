---
title: "Error BusyBox, no troba el disc a l'arrencar"
date: 2010-05-27
forum: Catalan Team
---

### Post by Lluís Martí on 2010-05-27
bona nit, companys

fa uns dies vaig actualitzar de la 9.10 a la 10.04 amb el gestor d'actualitzacions i en principi tot va anar com una seda, fins que al cap d'uns dies em vaig trobar que, després d'arrencar el grub i mostrar el logo en blanc d'ubuntu, s'interrompia la càrrega i passava a mostrar un missatge del tipus:

```
*****
Gave up waiting for root device. Common problems:
-Boot args (cat /proc/cmdline)
-check root delay = (did the system wait long enough?)
-check root = (did the system wait for the right device?)
- Missing modules (cat /proc/modules; ls /dev)
ALERT! /dev/disk/by-uuid/4947b5a1-7c2e-432c-ade5-ebebe7af92e7 does not
exist. Dropping to a shell!
Busybox v1.13.3 (Ubuntu1:1.13.3-1Ubiuntu7) built-in shell (ash)
(initframs) _
******
```

buscant per internet vaig trobar una solució que em va funcionar més o menys bé: editar l'arxiu etc/fstab reemplaçant la línia que fa la crida a la partició mitjançant UUID pel nom assignat a la partició, una cosa així:

```
#UUID=4947b5a1-7c2e-432c-ade5-ebebe7af92e7 /               ext3    relatime,errors=remount-ro 0       1
/dev/sda1 / ext3 relatime,errors=remount-ro 1 0
```

és a dir, que al final l'ordinador va acabar funcionant, sense entendre el motiu pel que es va produir aquest error. d'entrada vaig pensar que el disc dur havia dit prou cansat de les nombroses apagades per sorpresa que li han perpetrat els dos mocosos que corren per casa, però avui m'ha pujat la mosca al nas perquè s'ha produït el mateix error al portàtil de la meva companya, que encara funciona amb la versió 9.10 i que ha estat més ben tractat que no pas l'altre.

la sorpresa ha estat que després d'editar el etc/fstab i que hagi tornat a funcionar, he desfet els canvis recuperant l'arxiu original per veure si es reproduïa l'error, i ara tot torna a funcionar correctament (?!)

com que pel que he pogut llegir sembla que és més recomanable definir les particions amb UUID que no pas amb el nom, ho he tornat a deixar tot tal i com estava, però em sentiria millor si algú em pogués explicar quina pot ser la causa que provoca aquests errors; en principi no li faig gaires marranades a l'ordinador, però potser estic fent alguna cosa equivocada.

gràcies!

---

### Post by wgarcia on 2010-05-29
És estrany, una possibilitat que se m'acut és que hi hagi un sector del disc malament, i que quedi penjat en llegir-ho i s'esgoti el temps esperant, i que no trobi el sector danyat en cada arrencada, però és estrany que li hagi passat també a la teva dona, perquè no sembla massa normal que de sobte aparegui aquest sector (el sistema ja va verificant els discos periòdicament). 

Per forçar una verificació dels discos a la següent arrencada, es pot donar la següent instrucció des d'una línia de comandes:

sudo touch /forcefsk

---

