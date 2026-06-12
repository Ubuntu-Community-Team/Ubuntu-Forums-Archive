---
title: "arreglar disc dur"
date: 2007-06-19
forum: Catalan Team
---

### Post by collons on 2007-06-19
Hola, dos  preguntes que barrejan software i hardware, el mes passat va marxar la corrent elèctrica 283 vegades, aquí hi ha gent es compra un regulador de tensió per endollar els aparells electrònics que són els que més pateixen, però sembla que s'han d'instal·lar punyetes al huin2us, naturalment. 

Pregunta, funcionen en Linux només endollant l'ordinador a la caixa reguladora de tensió?

...per que tinc entès que quan marxa la llum t'envia una senyal per que guardis les dades i apaguis l'ordinador, en cas de que que no existeixi cap programa, eventualment put tenir una bombeta baix consum, quan s'apagui tancar l'ordinador.

Tinc cinc ordinadors només amb Linux, no utilitzo huin2us.

La segona pregunta força evident, 
Com es pot arreglar els discs durs amb aquests tipus d'errors, els símptomes son: 
quan el disc dur és nou funciona bé, 9 ò 14 mesos desprès, de cop l'ordinador es queda penjat o s'apaga sense més ni menys, el tinc com segueix:
/dev/hda1             ext3
/dev/hda2             extended
/dev/hda5             linux-swap

No hi ha cap informació a perdre, he intentat formatejar-lo amb MS-dos des de la disquetera però es queda penjat a la meitat.
quan faig:
iniciant live-cd kubuntu feisty

ubuntu@ubuntu:~$ sudo fsck -t ext3 /dev/hda
fsck 1.40-WIP (14-Nov-2006)
e2fsck 1.40-WIP (14-Nov-2006)
Couldn't find ext2 superblock, trying backup blocks...
fsck.ext3: Bad magic number in super-block while trying to open /dev/hda

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>

---

### Post by papapep on 2007-06-19
> Pregunta, funcionen en Linux només endollant l'ordinador a la caixa reguladora de tensió?

A veure, funcionar funcionen, en el sentit de que alimentaran el teu sistema en cas de manca de flúït elèctric.

> ...per que tinc entès que quan marxa la llum t'envia una senyal per que guardis les dades i apaguis l'ordinador, 

Just ahir un altre ubuntaire va publicar un article al respecte que pots trobar al planet.ubuntu.cat i al seu blog:

[http://arnau.alcalleop.cat/2007/06/18/sai/](http://arnau.alcalleop.cat/2007/06/18/sai/)

> Tinc cinc ordinadors només amb Linux, no utilitzo huin2us.

Ara ens comencem a entendre ;-)

> La segona pregunta força evident,
Com es pot arreglar els discs durs amb aquests tipus d'errors, 
No hi ha cap informació a perdre, he intentat formatejar-lo amb MS-dos des de la disquetera però es queda penjat a la meitat.

No has triat la millor eina precisament per a fer-ho :D

> quan faig:
..... The superblock could not be read or does not describe a correct ext2
filesystem. If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
**e2fsck -b 8193 <device>**

A la part que t'he ressaltat en negreta trobaràs la comanda que et pot ajudar:

```
e2fsck -b 8193 /dev/hda
```

---

### Post by AlexMuntada on 2007-06-19
Amb el permís d'en papapep, voldria puntualitzar:
```
e2fsck -b 8193 /dev/hda1
```

---

### Post by papapep on 2007-06-19
Permisat, permisat...:D

---

