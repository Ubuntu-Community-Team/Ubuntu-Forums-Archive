---
title: "Firefox se cierra"
date: 2007-07-09
forum: Argentina Team
---

### Post by Oktubre on 2007-07-09
Hola Gente!!

Tengo instalado Ubuntu 7.04, y desde hace unos dias que el Firefox, ante ciertas paginas que abren pop-ups, se me cierra al querer disparar el pop-up.
Probe sacando el blockeo de pop-ups, agregando los sitios entre los sitios permitidos a abrir pop-ups, y limpiando la info privada (cookies, history, etc.) tambien por las dudas.

Ha alguien le ocurre lo mismo? Pense en ver en el log de Firefox a ver si dice algo pero no lo encontre, donde esta?

Gracias y Saludos.

---

### Post by Al_maverick on 2007-07-09
puede ser que los popups tengan flash? yo tengo ese problema con mi firefox. Ciertos sites con flash hacen que se me cierre el firefox y termino abriendolos con konqueror.

---

### Post by Oktubre on 2007-07-09
Me parece que si. Lo extraño es que solo con los pop-ups es el tema. Porque si el sitio tiene flash no pincha el Forefox.

Saludos

---

### Post by Al_maverick on 2007-07-09
proba lo clasico, correlo desde una consola, y fijate q error tira cuando abris el popup.

---

### Post by Oktubre on 2007-07-09
Hice la prueba, copio el resultado : 

[I]$ firefox 
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
Segmentation fault (core dumped)[/I]

No es muy descriptivo la verdad.

Saludos

---

### Post by marianom on 2007-07-09
Yo diría que lo corras con un bug-buddy (ingresá bug-buddy --help en la terminal para más datos) y repliques el error. Con eso, reportes un bug en malone.
O podes ver [aca]("https://bugs.launchpad.net/bugs/+bugs?field.searchtext=firefox") si ya no está reportado el mismo problema.

---

### Post by Oktubre on 2007-07-09
Hola, 

probe con el bug-buddy, este fue el resultado:

[I]~$ bug-buddy --pid=5678 --appname=firefox
"/usr/bin/firefox": not in executable format: File format not recognized
[/I]

Estare utilizando mal el bug-buddy?

Saludos

---

### Post by Al_maverick on 2007-07-09
el nombre del proceso es firefox-bin, no firefox. Ese puede ser el problema

---

### Post by Oktubre on 2007-07-10
Hola, 

intente varias veces, finalmente creo que esta es la forma correcta de ejecutarlo: 

*$ sudo bug-buddy --pid=5473 --appname=/usr/lib/firefox/firefox-bin*

Lo estoy ejecutando con el Firefox corriendo, me parece que lo tengo que ejecutar una vez que se me cerro el mismo, no?
Otra pregunta, una vez que genero el archivo con los mensajes de error, adonde lo debo reportar?

Gracias, y Saludos.

---

### Post by marianom on 2007-07-10
Lo reportás [aca]("https://bugs.launchpad.net/") y si, debería correrse cuando se dé el error (en teoría). Yo no encontré nada que se cierre en mi máquina (lamentablemente :)) como para estar seguro.

---

### Post by Oktubre on 2007-07-10
Gracias por la info. Voy a reportarlo y capturarlo cuando me ocurra nuevamente.

Saludos

---

### Post by tzulberti on 2007-07-10
A mi tambien me pasa... Pense que era porque me habia mandado algun error, pero veo que es comun...

---

### Post by Oktubre on 2007-07-16
Instale el Macromedia Flash Player 9 y se soluciono!

Saludos

---

