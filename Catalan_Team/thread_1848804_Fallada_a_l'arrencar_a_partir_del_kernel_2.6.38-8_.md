---
title: "Fallada a l'arrencar a partir del kernel 2.6.38-8 generic (11.04)"
date: 2011-09-23
forum: Catalan Team
---

### Post by Accidia on 2011-09-23
Quan arrenco ho he de fer amb el kernel 2.6.38-8 generic. A partir d'aquest se m'atura l'arrencada perquè sí i només es veu això a la pantalla: 

[http://imageshack.us/photo/my-images/36/imag0397r.jpg/](http://imageshack.us/photo/my-images/36/imag0397r.jpg/)

Merci!

---

### Post by wgarcia on 2011-09-23
No pots entrar tampoc en mode "recovery"?

---

### Post by Accidia on 2011-09-23
Si vaig amb el recovery mode quan arrenco les X des de la línia d'ordres al cap d'un moment apareix això:

[http://imageshack.us/photo/my-images/195/imag0399z.jpg/]("http://imageshack.us/photo/my-images/195/imag0399z.jpg/")

---

### Post by wgarcia on 2011-09-23
Pel que dius infereixo que amb el mode recovery et permet arribar a una línia de comandes, i aquí dius que "arrenques les X", suposo que amb 
```
sudo service gdm start
```
o alguna ordre semblant.

Pels missatges d'aquesta última pantalla falla el mòdul de la teva targeta gràfica, que sembla una ATI. No conec gaire aquestes targetes, però dues coses que se m'acuden:

1) provar de la línia de comandes que dius:

```
sudo dpkg-reconfigure xserver-xorg
```

2) no hi ha una opció al menú del mode "recovery" per reconfigurar la gràfica (em sembla que fa el mateix que poso a 1)

---

### Post by Accidia on 2011-09-23
El gdm ja estava en marxa, arrencava amb ```
startx
```

Com que m'heu donat la pista que era tema de gràfica he pogut entrar amb resolució mínima i activar els drivers restrictius d'ATI. 

Funciona percfecte! Gràcies per l'ajuda! :)

---

### Post by wgarcia on 2011-09-25
De res, si marques el fil de debat amb "Solved" (amb Thread tools un cop que l'obres) fas un favor perquè quedi com a referència per algú que tingui algun problema semblant.

---

