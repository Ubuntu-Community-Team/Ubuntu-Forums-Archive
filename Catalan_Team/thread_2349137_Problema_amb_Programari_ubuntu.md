---
title: "Problema amb Programari ubuntu"
date: 2017-01-11
forum: Catalan Team
---

### Post by rvprada on 2017-01-11
Hola, sóc totalment nou, he instal·lat Ubuntu 16.04.1 LTS en un Lenovo B50-10. El vaig instal·lar ahir i funcionava bé, però avui quan li dono a l'icona de Programari Ubuntu s'obre i immediatament es tanca. He reiniciat moltes vegades però segueix fent el mateix. Què m'aconselleu?

---

### Post by wgarcia on 2017-01-12
És possible que hagin quedat alguns fitxers corruptes que fan que el programa es tanqui. Per això convindria esborrar els fitxers temporals que crea aquest programa i veure si s'arregla. Per això obre una terminal (per exemple amb "Control-Alt-t") i un cop que s'obri entra:

```
rm ~/.local/share/gnome-software/*
```

Això esborrarà aquests fitxers temporals que es recrearan un cop s'iniciï "Programari". Fes un reinici per si un cal i prova a veure si ara el Centre de Programari s'obre.

---

### Post by rvprada on 2017-01-13
Ho he fet, i em fa el mateix. Valdria la pena reinstal·lar, ja que de fet no tinc res? com ho hauria de fer?

---

### Post by wgarcia on 2017-01-14
Abans de resinstal·lar, prova aquestes dues coses. Sempre des d'una terminal.

1) Reinstal·lar el programa:

```

sudo apt-get remove --purge gnome-software
sudo apt-get install gnome-software

```

2) Si després de reinstal·lar el programa, continua fallant, inicia-ho des de la terminal

```
gnome-software
```

i mira si deixa algun missatge de fallada.

---

### Post by rvprada on 2017-01-14
Moltes gràcies wgarcia. He fet això i ja funciona. No sé si té res a veure però abans l'icona era una bossa taronja amb una A i ara és una bossa grissa amb nou quadradets. Moltíssimes gràcies de  veritat.

---

