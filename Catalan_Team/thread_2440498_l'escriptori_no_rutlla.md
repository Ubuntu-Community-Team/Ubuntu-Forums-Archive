---
title: "l'escriptori no rutlla"
date: 2020-04-11
forum: Catalan Team
---

### Post by josep-maria on 2020-04-11
La pantalla de l'escriptori no em deixa ni crear cap carpeta ni cap arxiu ni ficar-ne cap des de fora. Si fas clic al botó dret, no passa res (hauria de veure el menú crea carpeta - crea llançadora - crea document...).
Si faig clic a llocs > escriptori, obre una finestra de títol escriptori. Puc fer-hi de tot, però no em deixa treure res de la finestra cap a la pantalla. Si arrossego un arxiu, el torna enrera.
És un PC nou, on hi he ficat l'ubuntu mate.

Ubutu 16.04.6
Linux 4.4.0-177-generic x86_64
Mate 1.12.1
intel core i3

---

### Post by wgarcia on 2020-04-12
Si obres una termina, i entres:

```
ls -l
```

què mostra per a la carpeta "Escriptori"? (o "Desktop", si no ha demanat que tradueixi els noms de les carpetes en instal·lar el català).

---

### Post by josep-maria on 2020-04-12
Diu:

drwxr-xr-x 3 lloll lloll 4096 abr 11 19:51 Escriptori

---

### Post by wgarcia on 2020-04-13
Això està dient que l'escriptori és escrivible i llegible. Per tant sembla que el problema és que el Mate no t'ensenya el que hi ha a l'escriptori. No faig servir aquest escriptori, però sembla que hi ha una eina que es diu "Mate Tweak", i aquí hi ha opcions per mostrar o no mostrar les icones a l'escriptori. Dona-li una ullada a veure si per alguna raó s'ha configurat a no ensenyar les icones d'escriptori.

---

### Post by josep-maria on 2020-04-13
Ara ja va bé. He fet això del tweak, i ha funcionat. 
Gràcies.

---

