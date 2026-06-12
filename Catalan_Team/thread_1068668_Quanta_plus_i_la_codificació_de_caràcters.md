---
title: "Quanta plus i la codificació de caràcters"
date: 2009-02-13
forum: Catalan Team
---

### Post by kukat on 2009-02-13
Com estic un poc rallat, a veure si m'explique.

He passat del Kompozer al Quanta Plus (ja que no m'anava el Kompozer i veig que no es veu solució a la vista) i a part d'estar molt content amb el QUanta Plus (molt efectiu i senzill!!!) sols tinc un problema...

Quan he fet avui una pàgina, els accents no m'ixen com ho tenia configurat al Firefox ( Occidental ISO-8850-1). Clar, al canviar-lo a Unicode UTF-8, es veuen correctament...

Però com ho faig per a que el QUanta Plus em faça correctament els accents? Lo normal es tindre el firefox amb Occidental, nO? ja estic rallant-me....
AJuda!  :)

---

### Post by lluisanunez on 2009-02-13
Lo normal (o potser diria, el millor) és que el Firefox llegeixi a la pàgina la declaració de joc de caracters.
Per exemple aqui al fòrum la pàgina diu: 
```
<meta http-equiv="Content-Type" content="text/html; charset=ISO-8859-1" />

```
I  a la pestanya del costat tinc una pàgina que diu:
```
<meta http-equiv="Content-Type" content="text/html; charset=utf-8" />

```
I totes dues es veuen la mar de bé, amb accents i tot.

Perquè les pàgines que fas tinguin una declaració de joc de caràcters, has d'anar a les propietats del document, o de la pàgina (ara no tinc cap Quanta a mà) i establir-hi el joc de caràcters.

---

### Post by kukat on 2009-02-19
No encontre per a que es veja en els dos formats...:(

En "Tools", "Encoding", tinc assenyalat "Western European (iso-8859-1)

i en "Settings" "Configure Quanta" en "Environment" tinc a "Default CHaracter Encoding", el mateix, "iso 8859-1" i Default DTD (que no se que és) "HTML 4.01 Transitional". 

Per cert, cada vegada que s'obri el Quanta em surt un missatge:
"Some applications required for full functionality are missing:

- KImageMapEditor [[http://www.nongnu.org/kimagemap/]](http://www.nongnu.org/kimagemap/]) - editing HTML image maps will not be available;
- Cervisia [[http://www.kde.org/apps/cervisia]](http://www.kde.org/apps/cervisia]) - CVS management plugin will not be available.

You may download the applications from the specified locations."

però això supose que són ampliacions del programa, no crec que tinga res a veure (això va per a altre post). Que per cert, tin el Cervisia instalat i l'altre també...però es veu que no ho pilla o tinc que configurar alguna cosa...


Salutacions i moltes gràcies!

---

### Post by RainCT on 2009-02-19
Comprova que al «head» del codi font de la pàgina hi hagi la següent línia i, si no hi és, pots afegir-la-hi tu mateix:


```
<meta http-equiv="Content-Type" content="text/html; charset=ISO-8859-1" />
```

---

### Post by kukat on 2009-02-19
Doncs ja està! Moltes gràcies!!! 
De vegades la solució més lògica no se'ns ocorre...i era eixa! :p

Moltes gràcies!

---

