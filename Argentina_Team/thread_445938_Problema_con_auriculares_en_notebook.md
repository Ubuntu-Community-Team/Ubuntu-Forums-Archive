---
title: "Problema con auriculares en notebook"
date: 2007-05-16
forum: Argentina Team
---

### Post by zspikes on 2007-05-16
Buenas gente!! como va?
Resulta q me compre una notebook nueva (:D:D:D:D) y vino con vista, asiq se lo revente de entrada y le puse feisty. Por suerte con un poco de paciencia le hice andar todo, wifi, video, etc...
Pero lo q quedo pendiente q no logro hacer andar es lo siguiente:

Cuando conecto los auriculares, se escucha tanto por éstos, como por los parlantes, cuando deberia dejar de escucharse por los parlantes.

Alguna idea? estuve tocando los conmutadores, pero sin suerte :(

Saludos!

---

### Post by Al_maverick on 2007-05-16
Probaste tocando los parametros en el alsa-mixer?

Que modelo de notebook? Cual es el chip de audio?

En realidad nunca me paso, pero esos datos van a ser importantes para el que te pueda ayudar.

---

### Post by zspikes on 2007-05-16
probe poner en la consola alsamixer y tocar un poco ahi, pero salen 4 volumenes y nada mas.
Tengo una Compaq Presario C518LA
con respecto al chip, es esto?
```
gera@ameli:~$ cat /proc/asound/cards
 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xd0340000 irq 21
```

Tengo un amigo con una dell q le pasa lo mismo, tendra algo q ver?

---

### Post by loopeando on 2007-05-18
Eso me pasaba a mi con una Lenovo 3000 N100 en Edgy, en Feisty no pasa.

Lo solucione desactivando la opcion "External Amplifier" en alsa-mixer

El problema se llama "audio jack sensitivity", busca en los foros a ver si hay alguna otra solucion.

Saludos.

---

