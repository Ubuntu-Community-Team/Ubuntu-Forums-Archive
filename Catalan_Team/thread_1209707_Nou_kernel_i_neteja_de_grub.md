---
title: "Nou kernel i neteja de grub"
date: 2009-07-10
forum: Catalan Team
---

### Post by simfomet on 2009-07-10
Hola de nou,

    obro un nou fil per un tema diferent ja que fa poc amb les darreres actualitzacions s'ha instal·lat un nou kernel si no vaig errat i ara al grub apareix la versió anterior i la nova. Ha desparegut la vella?, cal desinstalar-la o res per l'estil?, es pot netejar i com l'entrada de l'anterior kernel al grub?

Gràcies.

---

### Post by Pablitus on 2009-07-11
Hola Simfonet!

> Ha desparegut la vella?

No, no ha desaparegut, si tries aquest kernel al grub en engegar l'ordinador es carregarà aquest kernel.

> cal desinstalar-la o res per l'estil?

No cal desinstalar-la, de fet de vegades és util tenir més d'un kernel instal·lat i amb l'opció de triar-lo al grub per si amb una actualització el nou kernel "fa el ruc". Però si ho vols fer pots buscar el paquet al Synaptic i desinstalar-lo, [mira't això d'aquest mateix fòrum]("http://ubuntuforums.org/archive/index.php/t-949958.html").

> es pot netejar i com l'entrada de l'anterior kernel al grub?

Si. Pots editar a mà l'arxiu on hi ha les opcions del grub fent a l'intèrpret de comandes```
sudo gedit /boot/grub/menu.lst
```Ves amb compte editant aquest fitxer. Buscant a google trobaràs força informació. El més fàcil que pots fer, si per exemple d'aquí un temps tens quatre o cinc kernels diferents, és comentar les línies que no vols que es vegin al grub amb el símbol "#".

Per exemple:
```
title		Ubuntu 9.04, kernel 2.6.28-13-generic
uuid		ed2384d6-28f3-4f19-a970-fc36e48db6b5
kernel		/boot/vmlinuz-2.6.28-13-generic root=UUID=ed2384d6-28f3-4f19-a970-fc36e48db6b5 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-13-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-13-generic (recovery mode)
uuid		ed2384d6-28f3-4f19-a970-fc36e48db6b5
kernel		/boot/vmlinuz-2.6.28-13-generic root=UUID=ed2384d6-28f3-4f19-a970-fc36e48db6b5 ro  single
initrd		/boot/initrd.img-2.6.28-13-generic

#title		Ubuntu 9.04, kernel 2.6.28-11-generic
#uuid		ed2384d6-28f3-4f19-a970-fc36e48db6b5
#kernel		/boot/vmlinuz-2.6.28-11-generic #root=UUID=ed2384d6-28f3-4f19-a970-fc36e48db6b5 ro quiet splash 
#initrd		/boot/initrd.img-2.6.28-11-generic
#quiet

#title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
#uuid		ed2384d6-28f3-4f19-a970-fc36e48db6b5
#kernel		/boot/vmlinuz-2.6.28-11-generic #root=UUID=ed2384d6-28f3-4f19-a970-fc36e48db6b5 ro  single
#initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, memtest86+
uuid		ed2384d6-28f3-4f19-a970-fc36e48db6b5
kernel		/boot/memtest86+.bin
quiet

```

Les línies que fan referència al kernel 2.6.28-11-generic estan comencen amb "#", i el grub les interpreta com a comentaris i no les té en compte. (Crec que només caldria posar "#" davant de la línia de "title" i ja no sortiria)

Aquest fitxer té moltes més opcions: que no es vegi el menu del grub (per veure'l s'hauria de pitjar "esc"), el temps que tarda en arrancar amb l'opció per defecte, canviar l'opció per defecte, coloraines, etc.

Pots mirar-te [http://www.guia-ubuntu.org/index.php?title=Grub]("http://www.guia-ubuntu.org/index.php?title=Grub")

Fins aviat!!

---

### Post by brissels on 2009-07-14
Una volta has comprovat que la nova revisió del kernel instal·lada funciona correctament, no hi ha cap problema en desinstal·lar l'anterior (o anteriors).
Encara que ho elimines del menú del grub (menu.lst) continua instal·lat. 
La forma més segura és fer-ho des del synaptic (o apt-get),en desinstal·lar una revisió del kernel, també s'elimina l'entrada corresponent del menú del grub.

---

### Post by SiscoGarcia on 2009-07-15
> **brissels said:**
> Una volta has comprovat que la nova revisió del kernel instal·lada funciona correctament, no hi ha cap problema en desinstal·lar l'anterior (o anteriors).
Encara que ho elimines del menú del grub (menu.lst) continua instal·lat. 
La forma més segura és fer-ho des del synaptic (o apt-get),en desinstal·lar una revisió del kernel, també s'elimina l'entrada corresponent del menú del grub.

Això depèn de com l'eliminis, si només vols que no aparegui al menú d'arrencada potser en tens prou amb comentar (escriure-hi al davant #) les línies que en fan referència; però si el que vols realment és eliminar-lo i alliberar espai al disc també ho pots fer com explica el papapep a la segona entrada d'[aquest fil]("http://ubuntuforums.org/showthread.php?t=949958").

---

