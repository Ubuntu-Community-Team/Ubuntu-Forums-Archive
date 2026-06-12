---
title: "Visualitzacio rallas des de l'inici"
date: 2010-05-01
forum: Catalan Team
---

### Post by kioni on 2010-05-01
Bona tarda, avui he volgut instalar el Lucid a casa un amic meu, pero no hi ha hagut manera... 

He agafat el seu pc de sobretaula li he posat el boot sequence de la bios en cd primari perque el live cd funcioni, li he fet una verificacio per veure que el cd esta correcta, despres he intentat arrencar en el modo de prova perque el provi sense instalar-lo, tot va correctament fins que al final a l'hora de visualitzar-se l'escriptori es veuen rallas horitzontals blaves i blanques.
Si intento instalar-lo es veu el logo de ubuntu que va carregant pero al moment de veure el primer pas de configuracio, hi ha un pampalleg de la pantalla que la torna a deixar amb ralles blaves i blaques horitzontals.

EL cd live es la versio de 32 bits.

Es una mica fustrant perque en cap de les dues opcions puc veure res de l'escriptori per mirar de posar-li el controlador correcta ...

Te un pentium 4 i una targeta grafica NVIDIA Geforce 7300 LE, el monitor es un monitor HP de fa un any (aixi que problema del monitor descartat)

Alguna ideea de com solucionar el problema ? 

Gracies

---

### Post by wgarcia on 2010-05-02
Aquesta versió d'Ubuntu porta un nou mòdul per a les targetes NVIDIA (els mòduls "nouveau", que venen directament al nucli). 

Si tens algun altre monitor a mà, prova-ho amb un altre monitor. Que no sigui un problema de freqüències i aquestes coses amb el monitor que menciones.

---

### Post by kioni on 2010-05-02
Solucionat quan arrenca el sistema s'agafa l'opcio F6 i l'opico Nomodoset i es carrega el sistema amb l'imatge una mica mes gran del normal (icona ubuntu) i es veu correcta, llavors avisa sobre el controlador que fa falta i solucionat.

:guitar:

---

