---
title: "Error de lectura de tamaño de disco"
date: 2008-05-06
forum: Argentina Team
---

### Post by alejandro.mc on 2008-05-06
Asi estaba mi disco en el orden en que lo lean:

8.04 - Windows XP - Espacio sin uso (sin formato) - Swap

Decidi borrar el Windows porque ya no juego mas al Civ IV y era la unica motivacion para tenerlo, y aprovechar el espacio sin formato que tenia sobrando. Entonces que hice:

Le mande "Delete" (lo borre) con el Gparted desde el LiveCD a la partición de Windows. No formatee, solo la borré. Y puse "resize" (agrande la partición del 8.04 y se "chupo" todo el espacio libre que habia, es decir amplio la particion del 8.04 usando todo el espacio de la que estaba liberada inicialmente y del espacio borrado donde estaba Widows XP).

Todo genial, arrancó re bien todo funciona al pelo. Un solo tema. Cuando voy al programita que analiza el uso del disco no se en castellano, en ingles se llama "Disc Usage Analyzer" (esta en accesorios) me tira que tengo un disco de 146 GB. Imposible dado que mi disco en total es de 80 GB. 

Quisiera saber si esto se puede solucionar, o si se va a solucionar solo cuando arranque por 30 vez (o algo asi no me acuerdo cuanta en hardy, en gutsy era 17 creo) y haga un analisis forzado del disco y el sistema de archivos?

Saludos y gracias adelantadas!

---

### Post by clasificado on 2008-05-06
> **alejandro.mc said:**
> me tira que tengo un disco de 146 GB. Imposible dado que mi disco en total es de 80 GB. 

Aveces pasa cuando hay sistemas de archivo diferentes a ext3 montados, lo que cambia el concepto de espacio usado y /media pasaria a ocupar un montón. ocupa, si, pero en otro disco.

Soy usuario de Kde3, y dandole bton derecho / propiedades a una carpeta podés ver el espacio libre de esa unidad montada.

Si podes pedirle detalle a ese programa (presupongo que de gnome) **tratá de desglosar en qué se está llendo el espacio**, y por ahi llegas a ver si son unidades de red, punteros temporales muertos, etc.

En kde3 pasa bastante.

clasificado

---

