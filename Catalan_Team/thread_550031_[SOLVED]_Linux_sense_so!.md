---
title: "[SOLVED] Linux sense so!"
date: 2007-09-13
forum: Catalan Team
---

### Post by Dilov on 2007-09-13
**Hola!**

Després de molts anys sofrint amb windows per fi he decidit passar-me a linux ja que sembla que l'Ubuntu és un bon sistema operatiu.

El cas es que l'he provat des de cd i no aconsegueixo que soni res. Tinc una Soundblaster Audigy2 Platinum de fa uns anys que segons sembla l'ubuntu reconeix, però no funciona.
He probat un munt de solucions que he trobat en fòrums sobre problemes similars però només he aconseguit que funcioni encara pitjor...

Espero que algun crack em pugui donar un cop de mà en el tema, moltes gràcies amb antel·lació!

---

### Post by papapep on 2007-09-13
Fa ben poc hi ha hagut un fil molt semblant parlant d'un tema com el teu:

[http://ubuntuforums.org/showthread.php?t=527975](http://ubuntuforums.org/showthread.php?t=527975)

---

### Post by CarlesOriol on 2007-09-13
Pots explicar: *no aconsegueixo que soni res* i *només he aconseguit que funcioni encara pitjor...*

Això vol dir que et sona o que no?

Jo tinc una audigy 2 ZS platinum (sense cap mena de dubte la millor targeta de so d'aquest costat de la galaxia) i no he tingut cap problema per fer-la funcionar.

El fil que et recomana en papaper tracta d'una doble configuració de targetes de so en la bios (placa base + audigy)... pot ser aquest el teu cas?

---

### Post by Dilov on 2007-09-14
Hola,

primer de tot moltes gracies per les respostes. He provat la solucio del fil que vas dir papapep, pero ja ho havia intentat a partir d altres fils que parlaven del mateix i no funciona.
[I]
no aconsegueixo que soni res i només he aconseguit que funcioni encara pitjor...[/I]

Be, amb aquesta frase em referia a que provant de fer canvis en codecs nomes vaig aconseguir que no reconegues la tarjeta i mai he aconseguit que funcioni el so amb ubuntu.

Crec que potser el problema pot estar en que reconeix moltes tarjetes, o aixo sembla.

Quan vaig a Sound preferences en la versio anglesa a Default mixer tracks em dona quatre opcions.

VIA8235 Alsa mixer
Brooktreebt878 Alsa mixer
Audigy2 Platinum SB0240p Alsa mixer
RealtekALC655 rev0 OSS mixer

i a mes a mes en aquesta sessio, no m havia passat mai abans, quan teclejo alsamixer em diu
alsamixer: function snd_ctl_open failed for default: No such device

QUe hi farem...

Alguna idea?

Gracies!

P.S. Perdoneu perque estic escivint sense el teclat configurat i es una mica complicat trobar els simbols adequats.

---

### Post by papapep on 2007-09-14
....vols dir que el teu ordinador té quatre plaques de só???

---

### Post by CarlesOriol on 2007-09-14
Uau... sembla un bon merder, però no ho és.

VIA8235 Alsa mixer és la tageta de so de la placa base, hauria d'estar desactivada per bios ja que no l'usarem per res.

Brooktreebt878 Alsa mixer - Això és la entrada de so de la capturadora de video. D'entrada no ens ha de portar problemes.

Audigy2 Platinum SB0240p Alsa mixer - Aquesta és la bona

RealtekALC655 rev0 OSS mixer - El mesclador propi del ipset de la targeta de so en placa base. 

La so&#320;lució és fàcil i es el que et deia: **Deshabilita la targeta de so de la bios**

---

### Post by Dilov on 2007-09-14
Be, moltes gracies CarlesOriol i papapep per la vostra ajuda!

La solucio era senzilla. Desactivar la tarjeta de so integrada a la placa base perque provocava conflictes. I ja esta. I l error ha estat meu per pensar que ja estava desactivada i que no podia haverhi una solucio tant senzilla com canviar una linia a la bios. En certa manera em sento estupid per haver passat hores intentant modificar configuracions quan la solucio era facil... en fi... suposo que l explicacio mes senzilla era la mes raonable.

Salut! I llarga vida a aquest forum!

---

