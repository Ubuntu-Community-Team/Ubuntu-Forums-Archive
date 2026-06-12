---
title: "algunes tecles no funcionen"
date: 2018-07-02
forum: Catalan Team
---

### Post by josep-maria on 2018-07-02
De cop i volta, algunes tecles ja no funcionen: les sis de insert-supr-av.pag., i les quatre de les fletxes <--, -->.
No he fet cap canvi ni actualització. Tinc l'ubuntu 16.04.4 Xerus, i el Mate 1.12.1. El processador és un i3.

---

### Post by josep-maria on 2018-07-03
També he canviat el teclat, sense èxit.

---

### Post by wgarcia on 2018-07-04
No funcionen en absolut o en alguna aplicació en concret?

---

### Post by josep-maria on 2018-07-04
No funcionen mai.

---

### Post by wgarcia on 2018-07-05
Mira a la configuració, a mètode d'entrada, si estàs usant o si tens opció d'usar una cosa que es diu "ibus", això pot estar afectant algunes tecles.

---

### Post by josep-maria on 2018-07-05
On és això?
He mirat a sistema > preferències > maquinari > teclat, i no ho he trobat.

---

### Post by wgarcia on 2018-07-06
Hi ha una configuració que es diu "Menú avançat", em sembla que s'habilita des del Mate Tweak (no faig servir el Mate i no ho puc dir de segur). La tindràs habilitat per casualitat? Penso que deshabilita moltes tecles.

---

### Post by josep-maria on 2018-07-07
A: sistema > centre de control > mate tweak > interfície 
On diu "habilita el menú avançat", no hi ha cap marca.

---

### Post by wgarcia on 2018-07-08
Una altra possibilitat: Mira si als menús, a la zona de configuració, tens una opció que digui "Accés universal" o semblant. Aquí pot-ser a la secció "Apuntar i clicar" hi ha una opció perquè el teclat numèric sigui utilitzat per controlar la pantalla. Mira si està habilitat, i si és així, desshabilita'l.

---

### Post by josep-maria on 2018-07-09
Fent clic a: aplicacions > accés universal
surt: 
         lector de pantalla
         on board
         screen magnifier

Però cap dels tres no és "apuntar i clicar"

---

### Post by josep-maria on 2018-07-09
El teclat que no va bé és un hewlett-packard amb un jack lila. Hi he ficat un altre, un innobo amb un jack usb. I sí que funciona. Abans havia fet proves amb teclats de jack lila, i no anaven bé.

---

### Post by wgarcia on 2018-07-10
Si funciona a uns teclats i a uns altres no, aleshores no sembla un problema de mala configuració a nivell de sistema, sinó que està desconfigurat per a un teclat concret. El que pots provar és endollar el teclat que no funciona, i fer:

```
sudo dpkg-reconfigure keyboard-configuration
```

Aquí pots mirar si veus el teclat que vols configurar, provar els que més s'assemblin,  a veure si s'acaben de configurar les tecles que et falten.

---

### Post by josep-maria on 2018-07-10
He fet:      sudo dpkg-reconfigure keyboard-configuration
em demana triar el teclat
surten 6 teclats hewlett-packard, des de un mini110, sis dels omnibook, dos pavilion, i un zt11xx
però no surt el meu, que es diu kb-0316
he fet clic a:   pc genèric de 105 tecles Intl
he anat fent clics a les opcions
quan ha acabat, el teclat continua sense funcionar

Jo no he canviat pas el teclat, ha anat bé molt de temps, i de cop fallen algunes tecles
tampoc no havia tocat mai la configuració (sudo dpkg-reconfigure keyboard-configuration)

---

### Post by wgarcia on 2018-07-11
Sí, és estrany que hagi deixat de funcionar.

Una altra cosa que pots provar és esbrinar si no és un problema del teu perfil d'usuari. No sé si l'ordinador té un compte d' "invitat". O si pots crear un compte nou i provar en algun d'aquests comptes alternatius si el teclat funcionés, si ho fa confirmaria que hi ha algun problema amb el teu perfil d'usuari que ha desconfigurat el teclat.

---

### Post by wgarcia on 2018-07-12
Aquí alguns suggeriments més:

Centre de Control -> Maquinari -> Teclat -> Opcions

té algunes opcions per habilitar algunes tecles específiques.

Això que comentava en un dels primers missatges de verificar si està habilitat el mètode d'entrada "ibus", mira si ho pots veure a 

Centre de Control -> Suport d'idioma

---

### Post by josep-maria on 2018-07-16
He fet això de canviar d'usuari, he anat a "convidat", i he tornat al meu usuari, i ara ja va bé. Gràcies.

---

### Post by wgarcia on 2018-07-16
Misteris de la informàtica, no sé com això pot arreglar el problema, jo sols ho suggeria per veure si les tecles funcionaven fora del teu usuari per veure si era un problema amb el teu perfil d'usuari. Però si ho arreglat benvingut sigui.

---

