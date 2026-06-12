---
title: "OLIBOOK 710+particiones en ubuntu 7.04"
date: 2007-08-07
forum: Argentina Team
---

### Post by marcesneibrun on 2007-08-07
Hola A Todos Me Compre Una Olibook 710-430, Con Procesador Intel Celeron, Y 512 Mb, 80 Gb, Etc, Lee Y Graba Dvd, Esta Hermosa.
Me Vino Con El Windows Vista, Y No Me Permite Instalar Nada Asi Que Quiero Instalarle El Ubuntu 7.04, La Idea Seria Particionar El Disco Para Mantener Los Dos Sistemas, Mi Pregunta Es La Siguiente En El Momento De Particionar Hay 2 Formas Una Manual Y Otra Automatica, Si Quiero Seguir La Automatica Me Lo Coloca En El Espacio Libre Contiguo, Ahora ¿ Tengo Que Hacer Antes Una Particion En Windows O Me La Hace Ubuntu Automaticamente?????
Gracias
Marcelo

---

### Post by faktorqm on 2007-08-07
Hola, mira yo nunca use el automatico, siempre el manual. No se si tenes idea mas o menos de linux, pero si elegis manual, basicamente lo que tenes que hacer es, a la particion de windows (suponiendo que ocupa todo el espacio del disco), "achicarla" al tamaño correcto para tu disco (si tenes 80gb, recomiendo dejar 10 ó 15gb para win, entre 5 y 10gb para linux, entre 1 y 2gb para swap, el resto para datos).
La que va a ser de windows, tenes que poner el punto de montaje en /media/windows.
La de linux, simplemente en /
La de swap, no va a ningun lado en particular, simplemente le decis que la vas a usar como swap y ya.
y la de datos la podes mandar a /media/datos
podes obviar la particion de datos y poner al final linux y swap. Salu2!

---

### Post by facundocorradini on 2007-08-08
> **marcesneibrun said:**
> Hola A Todos Me Compre Una Olibook 710-430, Con Procesador Intel Celeron, Y 512 Mb, 80 Gb, Etc, Lee Y Graba Dvd, Esta Hermosa.
Me Vino Con El Windows Vista, Y No Me Permite Instalar Nada Asi Que Quiero Instalarle El Ubuntu 7.04, La Idea Seria Particionar El Disco Para Mantener Los Dos Sistemas, Mi Pregunta Es La Siguiente En El Momento De Particionar Hay 2 Formas Una Manual Y Otra Automatica, Si Quiero Seguir La Automatica Me Lo Coloca En El Espacio Libre Contiguo, Ahora ¿ Tengo Que Hacer Antes Una Particion En Windows O Me La Hace Ubuntu Automaticamente?????
Gracias
Marcelo

Entre las opciones de particionado automáticas, elegís la que dice 
"redimencionar la partición y usar el espacio sobrante" (o algo así). 
Te va a aparecer una simple barrita con la cual achicas el tamaño de windows, y en lo que queda libre se crea automáticamente una swap y una ext3 para el ubuntu.

Saludos

---

