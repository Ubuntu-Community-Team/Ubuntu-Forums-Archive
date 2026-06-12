---
title: "Corrupció del sistema de fitxers a la Jaunty"
date: 2009-04-12
forum: Catalan Team
---

### Post by RainCT on 2009-04-12
Bones,

Només volia dir que a la Jaunty (no sé exactament quan va començar, deu fer poc més d'un mes) el sistema de fitxers se'm corromp cada dos per tres (fins a varis cops al dia, podent-ho arreglar amb un fsck ja sigui a l'arrencada -si hi ha errors et deixa en una terminal- o en pitjor dels casos des d'un LiveCD o reinstal·lant si s'han corromput fitxers del sistema).

Ja li vaig comentar a algú però dient que era per l'ext4; aquest però sembla que és innocent, ja que amb ext3 també passa de manera que ara estic sospitant del kernel. Ara estic provant amb Debian i tant amb el kernel predeterminat què és el 2.6.26-13lenny2 com amb el 2.6.29-3~snapshot.13390 funciona bé (la Jaunty té el 2.6.28, que no he trobat empaquetat per a Debian), així que no és problema del disc dur.

En fi, si a algú més li passa que sàpiga que no està sol, i que m'ho digui (o si sabeu d'on treure un kernel 2.6.28 per a Debian també). Ah, i que consti que no és per espantar-vos ni res, no deixeu d'instal·lar-vos la Jaunty per aquest missatge ja que el més segur és que no us passi el mateix.

---

### Post by torracastanyes on 2009-04-12
Utilitzes 32 0 64 bits?


En aquest fil diu que podría estar relacionat amb l'rsync:

[http://ubuntuforums.org/showthread.php?t=1122904&highlight=filesystem+corruption](http://ubuntuforums.org/showthread.php?t=1122904&highlight=filesystem+corruption)

---

### Post by RainCT on 2009-04-12
64 bits, i no faig servir l'rsync, però els simptomes coincideixen (a part d'això del "Stale NFS file handler", a mi el sistema de fitxer em passa a mode de només lectura però al cap d'un temps si provo de llegir algun fitxer em dóna tot tipus d'errors).

Gràcies per la informació.

---

### Post by CarlesOriol on 2009-04-13
Insta&#320;lat les smart tools (crec que era smartctl) i comprova que no sigui un error físic del disc. (tens força numeros)

Jo tinc diversos ordinadors en proves amb l'ext4 i no tinc cap problema... al contrari... mai havien anat tant bé.

---

### Post by papapep on 2009-04-13
> al contrari... mai havien anat tant bé.

i quina és la millora que hi notes?

---

### Post by CarlesOriol on 2009-04-14
Corre més i carrega menys l'ordinador. Al contrari del driver ntfs que deixa la màquina fregida quan li demanes molta activitat.

---

