---
title: "canviar la brillantor en ubuntu 14.04"
date: 2014-08-25
forum: Catalan Team
---

### Post by diablessamariken on 2014-08-25
Hola ubuntaires

he actualitzat a la nova versió d'Ubuntu el meu portàtil Acer Travelmate 5760G i em trobo amb el mateix problema que quan vaig migrar a la versió 12.04. No puc modificar la brillantor de la pantalla, ni a través dels paràmetres del sistema, ni a través del teclat (Fn+fletxes).

En la versió anterior vaig aconseguir un paliatiu, podia modificar la brillantor de cada finestra de manera independent. Una mica precari però més valia això que res.

Teniu alguna idea de com ho puc modificar? 

Gràcies
Astrid

---

### Post by wgarcia on 2014-08-28
Quina targeta gràfica fa servir el teu ordinador? Si no ho saps ho pots esbrinar entrant a una terminal:

```
lspci | grep -i vga
```

---

### Post by diablessamariken on 2014-09-14
teclejant el que em suggereixes, la informació sobre la targeta gràfica és la següent:

00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
01:00.0 VGA compatible controller: NVIDIA Corporation GF119M [GeForce GT 520M] (rev a1)


Com ho veieu?

Gràcies
Astrid

---

### Post by wgarcia on 2014-09-16
Tens doncs el que es coneix com a sistema híbrid, amb dues targetes gràfiques, Intel i NVIDIA. Ara seria bo saber quins controladors estàs usant. Això es pot mirar a "Paràmetres del sistema" -> "Programari i actualitzacions" -> "Controladors addicionals". Mira si surt alguna cosa aquí.

---

### Post by diablessamariken on 2014-09-29
Copio aquí la informació dels controladors:

NVIDIA Corporation:
aquest dispositiu utilitza un controlador alternatiu:

s'està utilitzant X.Org X Server - Nouveau display server des de xserver-xorg-video-nouveau (programari lliure)


En tinc una bona llista d'altres opcions:

- NVIDIA binary driver - version 331.38 des de nvidia 331 (de propietat comprovat)
- NVIDIA legacy binary driver - version 304.117 des de nvidia 304 (de propietat)
- NVIDIA legacy binary driver - version 304.117 des de nvidia 304-updates (de propietat)
- NVIDIA binary driver - version 331.38 des de nvidia 331-updates (de propietat)

Espero pistes ;)

Gràcies

---

### Post by wgarcia on 2014-09-30
Estàs usant doncs el controlador lliure, nouveau, però tens a disposició els controladors propietaris, el més convenient seria el primer de la llista, 331.38 (de propietat comprovat). Per tant podries provar si usant aquest controlador propietari et funciona el tema de la brillantor, però estigues preparat per si en reiniciar l'ordinador hi ha algun problema gràfic que no et permeti arribar a l'escriptori per tornar a la situació anterior. 

Si et passés això pots entrar en mode recuperació, i al menú que surt escollir reconfigurar la gràfica. Hi ha també altres maneres per tornar a usar el controlador lliure si tinguessis problemes: entrant a una consola un cop iniciat el sistema i fent-lo des de la línia de comandes, però esperem que no passi i que puguis provar si et va millor el controlador propietari.

---

### Post by diablessamariken on 2014-10-05
Oh! he canviat el controlador tal com m'indicaves i ha funcionat! No he tingut cap problema a l'hora de reiniciar l'ordinador.

moltes gràcies!!

Astrid

---

