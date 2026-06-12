---
title: "se cuelga la instalacion!"
date: 2007-06-11
forum: Argentina Team
---

### Post by mauridd on 2007-06-11
Hola, he querido instalar Ubuntu 7.04, pero se me tilda! Bootea bien, me aparece el menu...y cuando le doy instalar aparece el cartel de Ubuntu y una barra de progreso q no se mueve.......y asi queda, no reacciona mas....

Me baje la version 6.06 y me hace lo mismo. Pero lo mas raro es cuando puse un live cd de la version 5.04...Andubo!

 Si alguien me puede ayudar por favor tengo muchas ganas de instalar ubuntu.

PD:Ubuntu Studio tampoco anda y los cds estan bien porq en otras pc funcionan bien.

Les paso a describir mi pc:

Intel Celeron D 2.53 Ghz
Mother Asus p4v8x-x
1 Gb Ram
Viedeo GeFrce 6200
HD 80 gb ide
HD 160 gb Sata
Capturadora Pinnacle Sudio Deluxe 9

---

### Post by guillermolisi on 2007-06-11
Nada mas como para sacar de juego el tema RAM, le pasaste el MEMTest que trae el CD ? Por las caracteristicas de la maquina que tenes deberia funcionar perfecto. Supongo que antes tenias Windows por lo cual descarto algun otro problema de interrupciones en conflicto.

Cuando instalas, lo haces con los parametros iniciales por defecto o modificas alguno, el de video por ejemplo ?

---

### Post by mauridd on 2007-06-11
tengo win xp instalado y quiero instalar ubuntu en otra particion, y no toco ningun parametro. Voy a probar el chekeo de mem.

---

### Post by guillermolisi on 2007-06-11
Esa otra particion esta en el disco IDE o en el SATA ?

Supongo que teniendo tanto espacio, 80 + 160 Gb, es de dimensiones generosas, cierto ?

---

### Post by mauridd on 2007-06-12
La particion es en el IDE y es de 30 gb, hice el test de mem y dio ok.

---

### Post by lavaramano on 2007-06-13
probaste instalar en "safe mode" ?
(o algo asi, ahora no me acuerdo bien como se llama la opcion) 

sino proba con algun alternate cd. es en modo texto, pero no es mucho mas complicado que el modo grafico

---

### Post by sdm_cacto on 2007-06-13
En la laptop de un amigo (hp pavilion dv9000) pasaba lo mismo y lo solucioné agregando el comando "noapic" en el menu de booteo del cd.

Si preguntas por qué no tengo idea, pero es un error tipico del bios de esta misma PC.

---

### Post by Nemesis Teufel on 2007-06-27
> **sdm_cacto said:**
> En la laptop de un amigo (hp pavilion dv9000) pasaba lo mismo y lo solucioné agregando el comando "noapic" en el menu de booteo del cd.

Si preguntas por qué no tengo idea, pero es un error tipico del bios de esta misma PC.

me pasa lo mismo con un hp dv6000. Donde y como haces para agregar el comando "noapic"?

---

### Post by valucha on 2007-06-29
> **Nemesis Teufel said:**
> me pasa lo mismo con un hp dv6000. Donde y como haces para agregar el comando "noapic"?
[COLOR="DarkOrchid"]Apenas te aparezca el menú con la cuenta regresiva (ese que dice "start or install ubuntu, install ubuntu n safe grafics mode, etc.." apretás F6, y así de la nada escribís "noapic" y le das enter.[/COLOR]

---

### Post by faktorqm on 2007-06-29
Hola, yo tuve un error parecido, y era cuando la lectora (cd/dvd) estaba en esclavo, en lugar de estar en master. no se si tiene algo ke ver. salu2!

---

### Post by vk-cdg on 2007-07-05
En mi caso la instalacion se cuelga en el paso siguiente que es el de Migrar e importar configuraciones (configuraciones de que?). La lista aparece vacía y no me permite presionar ninguno de los botones, ni siguiente ni nada. Se FRIZA la pantalla.

Que puede ser?
Probé haciendo partición guiado o manual. De cualquier forma pasa lo mismo. Tengo un disco de 20 gb exclusivo para Ubuntu. En el otro disco tengo el XP. Probé arrancar con el disco de XP desenchufado y pasa lo mismo.

No se que puede ser.

Estaba viendo que mencionaban un alternate CD. Ese de donde lo puedo bajar?
Yo tengo el CD original del 7.04

---

### Post by fetova on 2007-07-05
> **vk-cdg said:**
> 
Estaba viendo que mencionaban un alternate CD. Ese de donde lo puedo bajar?
Yo tengo el CD original del 7.04
Aca:

[http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)

Observa que en la parte de abajo de "Start Download" hay una caslla de verificacion que dice "Check here if you need the alternate desktop CD. This CD does not include the Live CD, instead it uses a text-based installer.", Tildala y ya ;)

Saludos :)

---

### Post by djthree on 2007-07-08
Lo que trata de hacer la instalacion es cargar tus perfiles de Win XP (favoritos documentos, etc..)  y los trae a Ubuntu, pero si te falla esa parate te recomiendo que le indiques al programa que no exporte los perfiles  y despues vos te traes a mano las cosas a tu session de Ubuntu, al menos esa me parece una idea buena para poder instalar el sistema y empezar a "juagar" un poco.
Saludos!

---

### Post by ideafix on 2007-09-01
a mi tambien se me cuelga en la pantalla de migrar... Tengo un disco con windows y el espacio hecho para Ubuntu. Tengo el dvd del 7.04. Porq queda colgado ahi? No puede leer bien la particion de windows? Hay alguna otra solucion?

---

### Post by por100pre1 on 2007-09-01
> **ideafix said:**
> a mi tambien se me cuelga en la pantalla de migrar... Tengo un disco con windows y el espacio hecho para Ubuntu. Tengo el dvd del 7.04. Porq queda colgado ahi? No puede leer bien la particion de windows? Hay alguna otra solucion?

Postea las especificaciones de tu PC para una mejor idea... :-k

---

### Post by ideafix on 2007-09-01
Mi pc es un celeron de 2.23, 256 RAM, disco de 80. 60 son de la particion NTFS de windows y 20 son "espacio no asignado". Estab viendo lo del alternate cd. En caso de tenerlo, como lo deberia usar? Por ahi si entiendo alguna forma de instalar en modo texto podria probar asi.

---

### Post by por100pre1 on 2007-09-01
Prueba [Xubuntu Alternate Install CD]("http://mirror.anl.gov/pub/ubuntu-iso/DVDs/xubuntu/7.04/release/"). Corre con pocos recursos y su instador es muy flexible. Ademas usa el entorno XFCE4 mas liviano que GNOME de Ubuntu y KDE de Kubuntu para tener mas recursos para tus tareas y menos gastos por parte del entorno. :)

---

### Post by ideafix on 2007-09-04
Gracias funciono de maravillias

---

