---
title: "idioma malament pàgines web"
date: 2009-07-09
forum: Catalan Team
---

### Post by Miquel Ubuntero on 2009-07-09
Bon dia.
Algunes pàgines web, com per exemple, [http://localhost:631](http://localhost:631), en obrir-les amb Firefox amb Ubuntu en Català hem surten en anglès. En canvi, amb ubuntu en castellà hem surten en castellà.
Es pot sol·lucionar que hem surtin en Català?
Gracies.

---

### Post by Tomàs M. on 2009-07-09
Sí. Però potser no depèn de tu. Si tens l'idioma ben configurat, cal que algú tradueixi la pàgina i configuri correctament el servidor. Si [http://www.debian.org/](http://www.debian.org/) et surt en català, ja ho tens bé. Si no, pots anar per exemple a [http://tomi.cat](http://tomi.cat) i seguir les instruccions (que només veuràs si no tens el navegador configurat en català)

Sort!

---

### Post by lpargemi on 2009-07-10
Hola

Jo ho tinc configurat en català i em passa el mateix: la pàgina del CUPS em surt en anglès. 

Suposo que aquesta pàgina (el port 631 del teu propi ordenador) deu ser a algun lloc, i no deu estar traduïda al català.

Algú sap on és aquesta pàgina dins del sistema? 

Jo tinc Intrepid, sense res especial (bé si, un servidor Apache, però per allà no ho he vist).

Lluís

---

### Post by oriolsbd on 2009-07-10
Aquesta pàgina es troba a "/usr/share/cups/doc-root". En el directori que us indico hi ha la versió en anglès, i hi ha un subdirectori per cadascuna de les localitzacions. No hi ha cap carpeta "ca".

El que no sé és com s'hauria de traduïr perquè es distrubuís amb el propi Cups. Potser el millor és posar-se en contacte amb l'equip de Cups.

Salut!

---

### Post by Miquel Ubuntero on 2009-07-10
Hola de nou.
Certament la pàgina de debian hem surt en Català.
L'altre qüestió de cups, donat que no se de que va, no hi puc fer res.
Salut! i gracies.

---

### Post by lpargemi on 2009-07-11
Possiblement és un off-tòpic com un casa, però:

> **oriolsbd said:**
> Aquesta pàgina es troba a "/usr/share/cups/doc-root". En el directori que us indico hi ha la versió en anglès, i hi ha un subdirectori per cadascuna de les localitzacions. No hi ha cap carpeta "ca".

El que no sé és com s'hauria de traduïr perquè es distrubuís amb el propi Cups. Potser el millor és posar-se en contacte amb l'equip de Cups.

Salut!

Si amb drets de root copies el directori de la llengua que vulguis al directori ca, i et poses dins i modifiques el fitxer "intex.html" canviant els texts a català, podràs veure l'aplicació en català.

De qualsevol manera no deixa de ser una nyapa. Segur que és millor oferir la traducció a l'equip de cups perquè la pengin als update que hi hagi.

Salut

Lluís

---

