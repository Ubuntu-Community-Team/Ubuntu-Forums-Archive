---
title: "Encara amb problemes de so al ubuntu 7.10"
date: 2007-11-14
forum: Catalan Team
---

### Post by Urfe on 2007-11-14
Hola!

Tinc l'Ubuntu actualitzat a 7.10

El so no em fuciona bé. Alguns dies s'escolta molt distorsionat. Vaig cambiar la configuració del só a ES1371 DAC2/ADC perquè si deixava la detecció autmàtica habitualment no es sentia res.

Però amb aquesta configuració molt sovint el so està molt distorsionat. Un altre problema és que no puc escoltar el so de videos google o youtube encastrats a pàgines web.

L'última vegada que vaig escriure sobre aquest problema algún va comentar que el so és un problema estable de ubuntu. Encara ho és amb la nova versió?

Gràcies.

---

### Post by cortsenc on 2007-11-14
Podriem començar per sapiguer quina targeta de so tens.

Pel que fa al so en vídeos encastrats, probablement sigui problema del plugin de Flash. Al firefox (a la barra d'adreces) i posa **about:plugins** i diguens quin plugin tens per extensions **swf** i quina versió és.

---

### Post by Urfe on 2007-11-14
Moltes gràcies per respondre, Cortsenc.

No recordo quina targeta de so tinc. He obert l'Administrador de dispositivos i m'ha sortit una llarg arbre de coses inintel·ligibles per mi. Hi ha llocs on diu audio com per exemple:
Ensoniq Audio PCI ENS1371 ALSA Control Device
No veig cap altre cosa que em recordi a una marca comercial. Potser és un altre lloc on de buscar la targeta de so.


D'altra banda no he entés molt bé lo del firefox. Haig de posar a la barra d'adreces about lugins amb la cara groga al mig? Com escric la cara groga que somriu?

Gràcies.

---

### Post by papapep on 2007-11-14
hehhe, no home...és que el fòrum no entèn segons què. Cal que posis a la barra d'adreces:

```
about:plugins
```

---

### Post by Urfe on 2007-11-14
Vaja, vaja, així que no cal la cara groga... Ara ja ho he entés.

Això és el que apareix amb l'extensió swf:

application/x-shockwave-flash 	Shockwave Flash 9.0 r48

---

### Post by Urfe on 2007-11-15
Hola.

Crec que ja he trobat la descripció de la targeta de so. Sembla que és una Creative Sound Blaster AudioPCI (ES1371,ES1373) (WDM).

Salut.

---

