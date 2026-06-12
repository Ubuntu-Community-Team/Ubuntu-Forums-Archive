---
title: "Error en el muntat de Secure Digital de 2Gb"
date: 2007-06-22
forum: Catalan Team
---

### Post by crazyserver on 2007-06-22
Hola,
acabo de comprar dos SD's de 2 Gb cadascuna i cap de les dues les puc muntar a l'ubuntu Feisty..
En muntar em diu això:
```
mount: /dev/sde1: No es pot llegir el superbloc
```
He provat fer i refer particions, formatar i tornar a fomatar, formatar amb la PDA... 
La PDA la reconeix perfectament i sense problemes

La taula de particions original estàva així:

```
Disc /dev/sde: 2059 MiB, 2059403264 octets
38 capçals, 37 sectors/pista, 1430 cilindres
Unitats = cilindres de 1406 * 1024 = 1439744 octets

Dispositiu Arrenc.   Comença       Acaba    Blocs    Id  Sistema
/dev/sde1               1        2861     2010543    6  FAT16
```

Després m'he adonat de que hi havia un missatge que no havia llegit:
```
Nota: La mida del sector és 1024 (no 512)
```

Ar la taula de particions està igual pero acaba en el cilindre 1430 i en posar-la a la PDA em diu que és d'1Gb

A més, he llegit [això]("http://ubuntuforums.org/archive/index.php/t-249756.html")

Vull muntar les SD's!!!!

Gràcies per avançat!

---

### Post by Tomàs M. on 2007-06-27
<OT on>
Dius que ara la pda et diu que és d'1 GB? Ostres, no sé pas, però, perdut per perdut (no sé amb què has formatat a la pda), pots provar de formatar amb SKTools (em sembla que la versió share t'ho deixarà fer); no crec que empitjori. El que diuen per aquests móns és que no facis servir el Pocket Mechanic, que la pots acabar de destrossar...
<OT off>

Bona sort...

---

