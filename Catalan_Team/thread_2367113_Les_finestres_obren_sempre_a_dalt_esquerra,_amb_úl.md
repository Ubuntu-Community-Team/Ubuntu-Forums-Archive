---
title: "Les finestres obren sempre a dalt esquerra, amb última actualització 16.04 LTS"
date: 2017-07-26
forum: Catalan Team
---

### Post by fvilaubi on 2017-07-26
Des de que el dilluns em va entrar la darrera actualització de la 16.04, totes les finestres s'obren a la posició (0,0) a dalt a l'esquerra, i no es veu la part superior on hi ha el títol de la finestra i els controls de tancat, minimitzar, maximitzar.

Si faig Alt+F7 (moure la finestra) puc arrossegar-la on vull, però si tanco i torno a obrir torna a (0,0).
Passa amb tots els programes (explorador de fitxers estàndard, thunderbird, Firefox, .....)

Sabeu si està documentat aquest comportament (no he sabut trobar info) i té algun remei?

Gràcies.
Francesc.

---

### Post by wgarcia on 2017-07-26
Mira a veure si s'ha desmarcat "Situa les finestres" al gestor de Compiz. Per fer-lo, primer instal·la el gestor de Compiz si no el tens instal·lat:

```
sudo apt-get install compiz compizconfig-settings-manager
```

Un cop instal·lat, obre'l (per exemple entrant "compiz" al traç). Un cop obert, a la barra esquerra, cerca i clica "Gestió de finestres", i a la finestra que s'obre, mira si està marcat "Situa les finestres". Si no està marcat, marca'l. Si està marcat i continua el problema, serà alguna altra cosa.

---

### Post by fvilaubi on 2017-07-26
He instal·lat el ccsm i certament el "Situa les finestres" NO estava marcat.
L'he marcat i ara sembla que les obre "com sempre".

Prometo que jo no he tocat aquest paràmetre (no tenia ni el ccsm instal·lat!) es "normal" que amb la darrera actualització s'hagi perdut?
Pot haver algun altre efecte que encara no he trobat?

Moltes gràcies per les indicacions.
Francesc.

---

### Post by wgarcia on 2017-07-27
No crec que hi hagi alguna altra cosa malament, simplement per alguna raó s'ha desconfigurat això (també es pot fer per altres vies, no sols el ccsm). Però m'alegro que s'hagi arreglat.

---

