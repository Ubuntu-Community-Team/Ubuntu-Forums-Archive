---
title: "No puc actualitzar a 18.04"
date: 2018-05-18
forum: Catalan Team
---

### Post by trinkus2 on 2018-05-18
Hola,

Tinc la versió 17.10 i vull actualizar a la Bionic, però em surt aquest missatge qaun ho intento

[B]xxxxx@xxxxxx:~$ sudo do-release-upgrade -dS'està cercant una versió nova de l'Ubuntu
Les actualitzacions a la versió de desenvolupament sols estan 
disponibles per a la versió suportada més recent.
[/B]
Algú sap què passa? Ja heprovat algunes coses evidents i no xuta res

Gràcies per endavant
[LEFT][COLOR=#000000]sudo do-release-upgrade -d

Más información en:  [https://www.profesionalreview.com/2018/04/27/como-actualizar-a-ubuntu-18-04-desde-diferentes-versiones-anteriores/](https://www.profesionalreview.com/2018/04/27/como-actualizar-a-ubuntu-18-04-desde-diferentes-versiones-anteriores/)
[/COLOR][/LEFT]

---

### Post by wgarcia on 2018-05-19
Em sembla que no cal l'opció "-d", perquè això és quan encara no s'ha alliberat la versió definitiva. Un cop s'ha alliberat es pot actualitzar amb:

```
sudo do-release-upgrade
```

o si tens interfície gràfica, 

```
update-manager
```

t'hauria de dir que hi ha una nova versió disponible.

---

### Post by trinkus2 on 2018-05-19
Sí era això... merci!

---

### Post by wgarcia on 2018-05-20
Perfecte, si pots posa-li "Solved" a aquest fil, ho pots fer editant el teu primer missatge i veuràs una pestanya per posar-li aquesta etiqueta.

---

