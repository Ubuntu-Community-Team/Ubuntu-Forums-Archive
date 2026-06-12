---
title: "[SOLVED] Problema al apagar - Otra vez!!"
date: 2008-03-12
forum: Argentina Team
---

### Post by Tosh78 on 2008-03-12
Hola gente! Como estan? Bueno, posteo porque volvio a surgirme el problema de apagara. Esta vez, no instale nada nuevo. El tema es asi:
cuando le doy al boton de apagar, se cierra ubuntu, la barrita naranja se descarga quedando negra, pero despues aparecen los siguientes carteles
NetworkManager: <info> Desactivating device eth1.
NetworkManager: <info> SUP: sending command 'DISABLE_NETWORK 0'.
y queda ahi...No se apaga. Si pongo reiniciar, si se apaga, y obviamente, vuelve a arrancar la maquina. 
Yo edite el archivo del kernel boot y le puse al final acpi=force. Estoy funciono un par de dias pero ahora ya no. Antes de tener este problema me funcionaba todo con normalidad hasta que instale el ntfs-config y ahi empezaron a los problemas. Despues de eso no instale nada mas.
Mi maquina es una laptop con un procesador centrino de 1.7 y un 1gb de ram, y la version que tengo es la 7.10
Si pueden darme una mano, se los agradeceria, saludos!

---

### Post by niko_3100 on 2008-03-12
en el menu.lst del grub pone nosplash asi no te aparece la barrita naranja sino los procesos que va apagando. Proba con estos comandos desde una terminal sudo halt, otro.... sudo shutdown -h now      aclaro -h es el tiempo que queres que se apague como es now se apaga ahora, si pones -h 16:45 se va a apgar a esa hora y si pones -h 5 va a tardar cinco minutos en apagar, es una cuenta regresiva digamos.

---

### Post by Apokalyptica79 on 2008-03-12
Hola Tosh78, encontré algo a ver si te sirve:
Hacé **nano /etc/modules** y al final del fichero poné **apm power_off=1**, lo guardás y lo cerrás.
Ahora tenés que modificar el *menu.lst*, **nano /boot/grub/menu.lst**, buscás la opcio con la que carga habitualmente ubuntu y al final de, por ejemplo:
[I]
kernel /boot/vmlinuz-2.6.20-15-generic root=UUID=15397d47-9855-44af-9009-72f157a9b33f ro quiet splash
[/I]
Ponés lo siguiente **acpi=off apm=power-off**
Quedando de la siguiente manera:
[I]
kernel /boot/vmlinuz-2.6.20-15-generic root=UUID=15397d47-9855-44af-9009-72f157a9b33f ro quiet splash acpi=off apm=power-off
[/I]
Guardás y cerrás y para verificar si esto funciona correctamente reiniciá la pc y probalo.
Espero que te sirva.
Saludos.

---

### Post by niko_3100 on 2008-03-12
que hacen esos dos comandos acpi=off y apm=power-off ??? Estaria bueno saber por ahi te desactiva algo importante.

---

### Post by faktorqm on 2008-03-12
conoces wikipedia niko?

[http://es.wikipedia.org/wiki/APM](http://es.wikipedia.org/wiki/APM)

[http://es.wikipedia.org/wiki/Advanced_Configuration_and_Power_Interface](http://es.wikipedia.org/wiki/Advanced_Configuration_and_Power_Interface)

basicamente controlan la energia del equipo, es decir, desde el bios tenes opciones para suspenderlo en un tal tiempo, en apagar el monitor, en como apagarlo, si apaga los discos rigidos, si podes prender la compu desde la placa de red, o desde el teclado, controla cuando apretas el boton de power si es lo mismo que ir a apagar o si se apaga al toque o si se suspende.
Como veras no es taaaan importante. pero con apm existen algunos conflictos entre versiones, y con acpi en teoria no deberia haber problemas, solo que crean el hardware para windows tonces se complica. salu2!

---

### Post by pante on 2008-03-12
> **faktorqm said:**
> conoces wikipedia niko?


Me parece que el sarcasmo está de más. Por favor mantengamos la paz en el foro. Quien quiera ayudar que ayude sin mofarse del ayudado. Y nadie aprende si no sabe lo que hace ni por qué lo hace.

Saludos:)

---

### Post by faktorqm on 2008-03-13
sin palabras. perdon si les parece ofensivo, capaz fue del momento. 
las cosas OBVIAS me dan la sensacion de falta de voluntad, entendes? por eso lo digo

---

### Post by Apokalyptica79 on 2008-03-13
Hola, respondiendo a lo que significa **acpi=off apm=power-off** me parece que es la siguiente.
Hay dos modos de gestión de energía, ACPI y APM. ACPI es más actual o más moderno y está activado por defecto en los kernel debian, por lo visto. Por lo visto hay una serie de placas que no se llevan muy bien con ACPI, y necesitan APM; por lo que hay que indicarle en el arranque al kernel que no use ACPI (ya que está activado) y sí APM (que es un módulo que ha de cargar, por eso lo añadimos en /etc/modules).
Creo que esto sería la explicación a tu pregunta y el motivo por el cual se lo coloca en el grub.
Repito no estoy muy segura pero investigando parece que es así, obviamente que alguien que sepa más puede dar una mejor explicación al respecto.
Saludos.

---

### Post by Tosh78 on 2008-03-13
Hola!! Gracias a todos los que respondieron!
Por ahora no me funciono, lamentablemente. Aunque se  me funciono en parte. Que es esto? Que si apago pasado poco tiempo desde que arranco la maquina funciona bien, pero si paso un poco mas de tiempo, como no se, por ejemplo 15 miuntos o media hora, sigue tildandose.
Alguna sugerencia?

---

### Post by niko_3100 on 2008-03-13
Probaste con los comandos que te pase? sudo shutdown -h now??? o sudo halt?

---

### Post by Tosh78 on 2008-03-18
Si, Niko, tambien probe con eso...la verdad es que no funcionaba ninguna de las opciones ni tampoco las que encontre en google, asi que me harte y reinstale. Quizas no fue lo mejor visto, pero ahora se apaga. No se si dejar el post abierto o no por si alguien en algun momento llega con una solucion salvadora, ya que me gustaria saberlo, pero tampoco me parece bien dejarlo como solved, cuando en realidad no se resolvio.

---

