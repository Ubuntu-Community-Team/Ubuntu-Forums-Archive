---
title: "Executar aplicacions"
date: 2012-03-28
forum: Catalan Team
---

### Post by rosa d'abril on 2012-03-28
Hola,
Com es fa per executar un arxiu tipus: executable (application/x-executable)? Fent un doble clic al damunt no rutlla...
Gràcies

---

### Post by wgarcia on 2012-03-29
Si és un fitxer executable de Windows no es podrà executar a Linux. Tens seguretat que és per a Linux?

---

### Post by rosa d'abril on 2012-03-30
Doncs no, però no pateixis: vaig estar cercant per la xarxa i per esbrinar com es feia i vaig aprendre unes quantes coses, per exemple a moure'm pels directoris i executar aplicacions des del terminal. A poc a poc.
En qualsevol cas, aquest arxiu presumptament executable no devia ser ni una cosa ni l'altra perquè no responia a res. No era important i finalment l'he esborrat.
Gràcies

---

### Post by wgarcia on 2012-03-31
A vegades quan es baixa un fitxer executable, no té permisos d'execució i per això Linux no l'executa. Això es pot mirar clicant amb el botó dret sobre la icona del fitxer i mirant els permisos, o ara que et mous amb a línia de comandes donant la següent instrucció:

```
chmod u+x <nom del fitxer>
```

Tot i que sempre s'ha d'anar amb compte d'executar programes de procedència desconeguda.

---

### Post by rosa d'abril on 2012-04-02
Gràcies, 
Tot i començar a fer els primers balbucejos amb el terminal, encara estic a les beceroles i desconeixia la instrucció (una més a afegir al manual personalitzat que estic recopilant).
Salut!

---

