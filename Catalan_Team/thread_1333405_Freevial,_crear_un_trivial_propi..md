---
title: "Freevial, crear un trivial propi."
date: 2009-11-21
forum: Catalan Team
---

### Post by PellRoja on 2009-11-21
Amb uns amics juguem de tant en quan a al trivial que tenen per casa. És el  típic trivial que de tant en quan es dispara una pregunta de "toreros" o de esports d'anys antics.

M'agradaria poder crear pròpies categories en el freevial, per crear un trivial de preguntes que coneixem més entre els nostres amics. Com es poden crear noves categories i noves preguntes? es poden editar des de un fitxer o s'ha de compilar de nou el joc?

Com fa per poder iniciar un joc, sols amb unes categories en concret?

Salutacions :P

---

### Post by papapep on 2009-11-21
A les últimes versions que jo vaig controlar, que no sé si són les que hi ha als repositoris, es podia crear tantes categories com volies amb fitxers de text (en format xml si no recordo malament), que les contenien. Després podies triar 6 categories (ni més ni menys) al joc.
No em preguntis més per ara, que fa més d'un any d'això i tinc la memòria volàtil :D. Intento trobar-ho, o preguntar a qui pot estar al cas de com va i t'ho comento.

---

### Post by RainCT on 2009-11-21
Les preguntes es fan amb fitxers XML (un per categoria). Pot haver-hi tantes categories com es vulgui, però per al joc cal triar-ne exactament 6 (això es fa ab la tecla F3 durant la creació d'equips). Cadascuna de les preguntes pot tenir a partir de dues respostes, però se'n poden escriure més (tant de correctes i d'incorrectes) i el Freevial en triarà tres a l'atzar cada cop.

Mira't els fitxers que venen amb el Freevial (a /usr/share/games/freevial/databases/ca/) per veure el format (també hi ha un editor web, [http://db.freevial.org](http://db.freevial.org), però és només per a les preguntes que venen junt amb el Freevial i les preguntes noves han de ser acceptades per un moderador del lloc).

Per escriure les preguntes simplement crea un directori, crea-hi un fitxer XML (seguint l'exemple dels que venen amb el Freevial) per a cada categoria que vulguis i llavors inicia el Freevial des de la terminal fent «freevial --database ~/directori/on/tinguis/els/fitxers/xml". Llavors pots fer F3 i, a més de les categories estandard, hi haurien de sortir les teves.

Si alguna cosa no ha quedat clara, pregunta :).

---

