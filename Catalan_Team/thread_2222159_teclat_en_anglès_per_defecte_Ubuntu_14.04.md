---
title: "teclat en anglès per defecte Ubuntu 14.04"
date: 2014-05-05
forum: Catalan Team
---

### Post by fvilaubi on 2014-05-05
Al actualitzar Ubuntu Desktop 64 bits de 13.10 a 14.04, ha tornat a aparèixer el problema que ja em semblava resolt a 13.10 (veure el meu fil pel 13.10)
En sabeu alguna cosa més?
He fet el mateix, be de fet ho he deixat com estava, doncs al actualitzar ja ha quedat marcada l'opció que vaig comentar al meu fil anterior.

Francesc.

---

### Post by wgarcia on 2014-05-05
Et surt un cop ja has entrat a l'escriptori com a usuari? A mi em surt a la pantalla d'entrada, però no a la sessió d'usuari.

---

### Post by fvilaubi on 2014-05-05
Als dos. El que passa es que a la d'entrada no uso ni accents ni caràcters especials, i si va malament no ho noto.
A la d'usuari com tinc marcat el "checkbox" d'abaix a l'esquerra que diu "Show current input source in the menu bar" suposso que per això també ho veig.
La sol·lució es tan senzilla com marcar "ENGLISH" i directe i sense parar "CATALÀ" (que és el que em ve marcat per defecte) i ja funcionen totes les tecles bé (no a l'anglesa).
Fent el que vaig comentar al anterior post de la 13.10, ja no vaig tenir més soroll.... però sembla que el problema es més profund.

Francesc.

---

### Post by wgarcia on 2014-05-06
No m'ha quedat clar si ara ho has arreglat o no, jo no ho veig i no he tocat res quan vaig actualitzar a la 14.04.

---

### Post by fvilaubi on 2014-05-10
NO ho tinc arreglat. La sol·lució que a la versió 13.10 em va funcionar (posar fonts diferents per finestra, i la font actual per lafinestra nova) amb la 14.04 NO.
El que continua funcionant com a la 13.10 es simplement fer clic a "anglés", i tornar a fer clic a "Català", sense ni tan sols tancar la finestre emergent que surt al posar el focus al quadre d'idioma.
Actualment just després d'obrir l'usuari ja vaig sistemàticament al idioma faig la maniobra que he explicat i el teclat funciona perfecte, si no el tens en perfecte anglés: & al 7, el ; al lloc de la ñ, etc.

Al entrar al usuari, pots veure que a la barra de dalt,al costat de xarxes, tinc l'idioma del teclat. Per terure'l, si desmarco el checbox d'abaix a l'esquerra, ja no el tinc a la barra. Per recuperar-lo haig d'anar per "Paràmetres del sistema" > "entrada de text", i tornar a marcar.

Com pots veure també el català el tinc primer. I ha gent que comenta que això pasa per tenir-lo com segon, llavors està clar que el primer es l'anglés. Però no es el meu cas. Quan engega el tinc amb "Es" (Català).

Qualsevol idea o sugeriment es benvingut!
Francesc.

---

### Post by wgarcia on 2014-05-12
Has provat si també et passa amb un altre usuari a la màquina? El més fàcil és provar-lo amb l'usuari "guest" si el tens habilitat.

---

### Post by fvilaubi on 2014-05-21
Perdona Wgarcia, he estat una setmana fora i no he pogut fer el seguiment.
A dia d'avui HA CANVIAT la forma que treballa aquest selector, entenc que com a conseqüència de l'última actualització del Ubuntu.
En aquests moments al obrir l'usuari, sense haver canviat res, em presenta el teclat en anglès "En", encara que a dalt de tot tinc el català (veure imatge annexa del #5). Segons la documentació la selecció primera es la de dalt de tot, llavors per que agafa la segona?

Tens identificat algun bug sobre aquest tema que s'hi estigui treballant? (penso això pel canvi que he tingut en el comportament del selector)

---

### Post by wgarcia on 2014-05-21
Et passo una solució que van suggerir a la llista de correus. La solució és per a Lubuntu, però jo crec que pot funcionar també per a Ubuntu.  

"Si vas a preferències/ Mètodes d'entrada del teclat, a dins vas a Mètode d'entrada, si tens activat el quadre personalitza els mètodes
d'entrada el desactives i borres totes les opcions, et sortirà un quadre que diu: La llista de mètodes d'entrada desats es buidarà
immediatament i cada cop es configurarà amb l'idioma d'entrada. Hi esteu d'acord?

després de acceptar ja funciona :P"

---

### Post by fvilaubi on 2014-05-23
No he fet res, amb les actualitzacions que em van entrar ahir vaig notar que les noves finestres obrien en anglès.... sospitós!
Llavors vaig anar als paràmetres d'entrada de text i vag posar que obrisin totes les finestres amb el defecte.... 
I ara va sense cap problema!

Esperem que aquest cop si que estigui trobat el problema i no torni a sortir a la 14.10  ;-)

Moltes gràcies pels vostres comentaris.

---

