---
title: "ATI Radeon HD 4570"
date: 2009-10-20
forum: Catalan Team
---

### Post by acoro on 2009-10-20
Hola! a tothom! 
L'altre dia em vaig instal·lar l'ubuntu 9.04  i mica mica vaig aprenent. Ara porto 2 dies mirant a veure si puc fer tirar la targeta gràfica aquesta per poder-me instal·lar la barra awn (que segons anava llegint em deia que necessitava tenir els gràfics en 3d nO?) i en resum per poder-la fer funcionar. He provat coses i no hi ha manera....He mirat a la pàgina d'ATI i tampoc, he intentat llegir coses amb anglès i he de reconèixer que soc bastant dolent...segons he llegit per la xarxa, les ati i l'ubuntu no son massa amigues nO?..algú em podria donar un cop de ma?¿ Us ho agraïré moltíssim!!!
Albert Corominas i Carles

---

### Post by kukat on 2009-10-22
Hola!!!

No se molt de la HD 4570, però si és per la barra AWN, pots provar de fer anar aquesta barra activant el "composite" , _sense activar_ el Compiz...

Solament tens que posar açò a la terminal:

```
gconftool-2 --type Boolean --set /apps/metacity/general/compositing_manager True
```

I ja anirà el AWN sense el Compiz! i més ràpid! :D

També es recomane que li pegues una ullada al Gnome-Do! Jo abans utilitzava la barra AWN, però ara gaste el GNome-Do per velocitat (tampoc tinc un pc gaire ràpid...)

Salut!

---

### Post by acoro on 2009-11-02
Ok perdona per contestar tant tard! ja m'ha anat bé!!! gàcies!


> **kukat said:**
> Hola!!!

No se molt de la HD 4570, però si és per la barra AWN, pots provar de fer anar aquesta barra activant el "composite" , _sense activar_ el Compiz...

Solament tens que posar açò a la terminal:

```
gconftool-2 --type Boolean --set /apps/metacity/general/compositing_manager True
```I ja anirà el AWN sense el Compiz! i més ràpid! :D

També es recomane que li pegues una ullada al Gnome-Do! Jo abans utilitzava la barra AWN, però ara gaste el GNome-Do per velocitat (tampoc tinc un pc gaire ràpid...)

Salut!

---

