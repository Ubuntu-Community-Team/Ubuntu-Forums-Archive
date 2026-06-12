---
title: "No s'obre el menú aplicacions"
date: 2009-07-13
forum: Catalan Team
---

### Post by bratac on 2009-07-13
Bones,

avui, no sé perquè ha deixat d'obrir-se el menú «Aplicacions» que hi ha a la part superior del gnome. L'he eliminat i he creat un menú nou i em passa el mateix. 

Tampoc puc gestionar-ho des de sistema> preferències> menú principal

i no em troba la carpeta aplicacions si vull fer enllaços directes a la barra superior pels programes més necessaris.

Algú em pot ajudar? Gràcies!

---

### Post by SiscoGarcia on 2009-07-14
Hola Bratac,

No sé si t'estic entenent bé, però pel que dius suposo que fas servir gnome; si és així, si tens el quadre superior, has provat de fer amb el botó contrari "+ afegeix al quadre"? Si ho pots fer, et surt l'opció "Menú principal"? Mira a veure què tal.

---

### Post by papapep on 2009-07-14
Ja ho va poder solventar amb una referència a un fòrum que li varen fer al canal d'irc, Sisco. Va dir que posaria la solució aquí quan tingués una estona.

---

### Post by SiscoGarcia on 2009-07-14
Bé, doncs esperarem a veure com se n'ha sortit ;)

---

### Post by bratac on 2009-07-15
Bones,

el primer que vaig fer va ser crear un nou menú amb el botó dret però el problema persistia. Després de demanar ajuda al xat vaig deduir que  els problema era que l'enllaç entre la icona d'Aplicacions i el seu origen estava trencat. Senzillament vaig verificar que el fitxer:

/home/nomusuari/.config/menus/applications.menu

era un fitxer buit.

Per solucionar-ho només va caldre eliminar el fitxer i reiniciar l'ordinador (de fet no sé si s'havia de reiniciar però jo ho vaig fer) després tot va tornar a anar fi com una seda.

Gràcies de nou al xat i disculpeu el retard en la solució.

---

