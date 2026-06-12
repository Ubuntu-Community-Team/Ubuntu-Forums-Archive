---
title: "Problemes amb els DVD DL"
date: 2011-09-27
forum: Catalan Team
---

### Post by lavinia.gac on 2011-09-27
Des de fa uns dies els dvd's de doble capa (DL) no es munten mentre els dvd's normals de 4,7 GB es detecten i munten a la perfecció. Abans mai havia tingut cap problema amb cap dvd, independentment que fos normal o de doble densitat. 
Ho he provat amb pel-lícules comercials en dvd de doble capa i en dvd's gravables DL i la unitat no es munta. Tinc dues distribuccions Ubuntu en el meu disc dur i en les dues em passa el mateix i abans no en tenia cap problema. 
He d'entendre que la unitat dvd està malmesa? 
El comandament de muntatge d'un dvd és diferent per a dvd's de 4,7 gb que per als de DL? Siguent mal pensats, es pot configurar un sistema gnu/linux de tal forma que no es muntin dvd's DL? Què pot haver succeït?

Moltes gràcies companys!

---

### Post by wgarcia on 2011-09-28
Has provat iniciant amb algun nucli més antic, que no sigui algun error del nucli actual que tens instal·lat? 

Em refereixo a intentar arrencar el sistema des del menú "grub" inicial des d'un nucli més antic.

---

### Post by lavinia.gac on 2011-09-28
Algun nucli més antic? Els kernels més actuals no poden muntar unitats amb dvd's DL?
Les distribucions ubuntu de l'ordinador són la 7.10 i la 9.10 (en ambdues crec que el kernel correspon amb un 2.6) i mai havia tingut problemes amb l'automuntatge de dvd's DL en la unitat lectora. Ara em passa que no es munten en cap de les dos.
Per cert, quina és l'ordre per mirar de muntar aquest tipus de dvd's de forma 'manual'?

Moltes gràcies

---

### Post by wgarcia on 2011-09-28
Si t'està passant en aquestes distribucions segurament no serà un problema del nucli, més sembla algun problema amb el maquinari. El que pots fer és provar amb alguna altra distribució o l'última que tingui Ubuntu des d'un CD Live o USB Live a veure si et reconeix la unitat, i si no ho fa començar a pensar que està fallant alguna cosa de maquinari. 

Allò del nucli t'ho deia perquè sí que pot passar que alguna versió específica del nucli introdueixi alguna "regressió" que faci que algun maquinari falli, i per tant val la pena provar algun altre nucli si el tens instal·lat per si un cas.

---

### Post by lavinia.gac on 2011-09-29
Gràcies, provaré de fer anar la unitat amb una distribucció tipus CD live o USB live a veure si munta dvd's DL.

---

