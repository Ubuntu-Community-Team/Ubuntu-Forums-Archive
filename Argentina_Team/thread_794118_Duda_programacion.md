---
title: "Duda programacion"
date: 2008-05-14
forum: Argentina Team
---

### Post by AzureSky07 on 2008-05-14
Se que esto no es un foro de programacion pero la verdad es que no estoy en ninguna comunidad con ese fin y como se que son varios los que saben programacion en C aca, bueno, almenos intento.

Estoy aprendiendo a programar en C y tengo la siguiente consulta: hay alguna forma de ubicar texto en pantalla deacuerdo a coordenadas que se les de?
Por ejemplo si quisiera que aparezca una linea de texto en la parte inferior derecha de la pantalla sin tener que  llenar la pantalla de espacios y \n

Saludos y gracias AzureSKy

---

### Post by faktorqm on 2008-05-14
instruccion gotoxy(x,y); no es ansi me parece. perdon pero me tengo ke ir a la facu. cuando vuelva si queres te expliko mejor sino buscala en google ;)

---

### Post by AzureSky07 on 2008-05-14
Es exacto eso lo que necesitaba ^^ muchas gracias, no tenia idea de como buscarlo.

Saludos AzureSky

---

### Post by Hernán-Amaya on 2008-05-14
gotoxy() no es ANSI C está en la biblioteca hecha por borland conio.h  ahí tenes varias cosas que te pueden ser útiles como wherex wherey pero ojo! como no son ansi puede que no sean portables. te dejo un link donde explica un poco mas el tema

[http://c.conclase.net/Borland/index.php](http://c.conclase.net/Borland/index.php)

---

### Post by tzulberti on 2008-05-14
> **AzureSky07 said:**
> Se que esto no es un foro de programacion pero la verdad es que no estoy en ninguna comunidad con ese fin y como se que son varios los que saben programacion en C aca, bueno, almenos intento.


Te comento que existe un foro de programacion aca mismo:
[http://ubuntuforums.org/forumdisplay.php?f=39](http://ubuntuforums.org/forumdisplay.php?f=39)

---

