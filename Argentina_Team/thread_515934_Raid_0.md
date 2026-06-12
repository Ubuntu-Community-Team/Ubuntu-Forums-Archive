---
title: "Raid 0"
date: 2007-08-02
forum: Argentina Team
---

### Post by enebarraene on 2007-08-02
buenas! tengo un mother asus p5v800 con 2 sata de 80 en raid 0. Para el XP, al momento de instalar me pide insertar un diskette para que me erconozca el raid. Con Ubuntu no puedo lograr que me reconozca el raid. Me toma los sata por separado. Necesito mantener el raid por la info que tengo. Álguien tiene idea cómo puedo solucionarlo? Gracias!.-

---

### Post by faktorqm on 2007-08-02
Hola, aca encontre un par de cosas, pero como nunca tuve dos discos en RAID no se si estan hablando del RAID por hardware o por software. Yo supongo que por hardware.

[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)

[http://www.ubuntu-in.org/wiki/SATA_RAID_Howto](http://www.ubuntu-in.org/wiki/SATA_RAID_Howto)

[http://www.howtoforge.com/linux_software_raid](http://www.howtoforge.com/linux_software_raid)

OJO con este que es para RAID 1, no para RAID 0:

[http://www.eslomas.com/index.php/archives/2007/02/22/configurcion-de-raid-y-lvm-en-ubuntu/](http://www.eslomas.com/index.php/archives/2007/02/22/configurcion-de-raid-y-lvm-en-ubuntu/)

Bueno, espero que te sirva. Te aviso por las dudas que esto lo saque de google igual, no son tutos que yo haya usado. salu2!!

EDITO: Lei por ahi que la version SERVER de ubuntu lo soporta de una. Capaz es cualquiera, fijate. salu2!

---

### Post by enebarraene on 2007-08-03
Buenísimo Muchas grax. Lo veo y desp te cuento!! Salu2!! Nacho.-

---

### Post by guillermolisi on 2007-08-04
Enebarraene

Cuando decis que tenes los discos SATA en Raid-0, a que te referis exactamente ? A que asi los ve WinXP o tenes hardware especial para lograr ese tipo de disposicion de discos ?

Esa mother trae algo on board para hacer Raid con SATA ?

La otra alternativa, no tan buena como la de Raid por hardware, es hacer Raid por software directamente con Linux cuando particionas los discos al instalar Ubuntu.

Me quedan algunas dudas respecto de si con esto te sirve como implementacion de alta disponibilidad ante la caida de uno de los discos.

---

