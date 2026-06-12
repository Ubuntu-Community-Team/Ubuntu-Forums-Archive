---
title: "No puedo iniciar Ubuntu!"
date: 2007-08-30
forum: Argentina Team
---

### Post by gakna on 2007-08-30
Hola a todos y disculpen si soy demasiado extenso en explicaciones, es que soy muy nuevo  Resulta que finalmente logré reconfigurar mi ATI 9250 y tener aceleración 3D. El tema es que instalé compiz fusion y funcionaba. Luego instalé los plugins no oficiales: "compiz-fusion-plugins-unofficial" para poder ver los efectos 3D que no me funcionaron por lo que los desactivé en el Compiz Manager. Luego, envalentonado instale unos temas de escritorio para cambiarle la apariencia (T-ish for Clearlooks y OSX iconset, y un fondo de pantalla y descargué un theme de iconos: Innex que no instalé), e intenté conectar y hacer un hotsync con mi palm y configurar el programa de palm que viene con el Ubuntu pero no lo logré asi que lo dejé. Ubuntu funcionaba bien aparte de esto. Al día siguiente al intentar prender la computadora veía la barra de ubuntu y luego...negro, la nada...no ingresaba al entorno gráfico. Entré en modo recovery y puse: "sudo /etc/init.d/gdm restart" y logré entrar!!!. Al iniciarse me mostró un error: "Failed to initialize HAL", pero por lo demás todo funcionaba, inclusive compiz fusion. Apagué nuevamente la computadora y nuevamente no pude entrar, pero esta vez, al intentar nuevamente desde el modo recovery el comando "sudo /etc/init.d/gdm restart" no funcionó, tampoco reconfigurar el xorg.org, ni nada, no consigo entrar al entorno gráfico. Alguna idea??? ya busqué bastante en el foro y google pero no encuentro nada. Muchas gracias a todos:)
PD: Tambien probé el comando sudo dpkg-reconfigure gdm y luego startx y lo mismo, funcionó una vez, pude reiniciar otra vez, pero cuando  apague la computadora y la volvi a prender nuevamente no entraba al entorno gráfico y ya no funcionaba el comando desde recovery mode :(

---

### Post by Mauro22 on 2007-08-30
Los errores de HAL son de la placa de video.


Me parece que tendrias que reinstalarlo.

---

### Post by msangil on 2007-08-30
Kcs Gakna,

Me parece que Mauro tiene razón. Por qué no corrés el Ubuntu desde Live CD y te hacés un backup (por las dudas) y reinstalás? Te va a llevar menos esfuerzo que tratar de arreglarlo.

Yo tengo ATI también y con todo el tema este de los drivers no le puedo poner nada. Yo ya no me caliento más. Espero a los nuevos drivers de xorg a ver si aparece una solución mágica.

---

### Post by gakna on 2007-08-30
Ok...a reinstalar entonces...:) pero como nunca lo hice unas preguntas...cuando el CD me ofrezca particionar el disco, como hago, o que opción elijo, para que se reinstale en la partición que creo Ubuntu inicialmente y donde se instaló la primera vez?? gracias!!!

---

### Post by Mauro22 on 2007-08-30
Cuando llegue la parte de particionar el disco, elije la opcion manual y luego:

* Si tienes otro S.O como Win2, te van a aparecer particiones tipo ntfs/fat. En este caso es facil ya que sabes que esas no las tienes que tocar.

Y luegos creas una particion con formato ext3, con punto de montaje en "/" sin las comillas, despues creas otra ext3, con el punto "/home" sin las comillas, y por ultimo una swap del doble de la memoria RAM.



Con eso ya estarias.! Las duda aqui abajo!

---

### Post by msangil on 2007-08-30
Mauro,

Tendrá algo que ver con el bug este que está en el Launchpad?
[https://bugs.launchpad.net/ubuntu/+bug/126810](https://bugs.launchpad.net/ubuntu/+bug/126810)

Gakna,
Vos no estás usando Gutsy 2007-07-18 i386, no?

---

### Post by Mauro22 on 2007-08-30
Msangil, eso puede ser, nunca especificó que versión de ubuntu instaló :confused::confused:

Gusty no esta en beta 5 ?? 


Por qué demonios instalan una version beta si saben que van a tener problemas!!! 

:mad:

---

### Post by gakna on 2007-08-30
Tengo instalado Ubuntu 7.04, creo que es la actual, no??

---

### Post by msangil on 2007-08-30
@gakna

Feisty? No, quedate tranquilo entonces. El bug creo que es exclusivo de Gutsy.

Si te aparece algún error durante la instalación avisá también por las dudas.

Los efectos visuales en Feisty mirá que son medio experimentales todavía. Si te mandás a ponerle 50 millones de addons y lo twekeás todo hay chances de que ALGO se te pueda escapar de las manos.
Si me permitís una sugerencia, yo en tu lugar instalaría el Beryl con los paquetes que te aparecen en los repositorios y no lo tocaría mucho más teniendo en cuenta que ya tuviste problemas.


@mauro
Zafamos, Mauro - no debe ser el bug ese entonces.

---

### Post by gakna on 2007-08-30
Muchas gracias! voy a intentar reinstalar, espero no hacer desatres, cualquier cosa los volveré a molestar! :)

---

### Post by msangil on 2007-08-30
Ningún problema. Las veces que haga falta. :)

---

### Post by gakna on 2007-08-30
Estoy justo reinstalando...antes de cometer ningún error (grave :):
Estoy en la parte donde dice "preparar particiones" en el modo manual.
Me figura lo siguiente:
  
/dev/sda1  ntfs   /media/sda1  235308mb   desc
/dev/sda2  est3  /media/sdas   14081mb     5100mb
/dev/sda5  swap                      666mb    0mb

Esto es lo que estaba de mi instalación anterior. El primero sería el de windows y no lo toco, Que hago con los otros 2??? Edito la partición? Borro la partición? o deshago los cambios realizados en las particiones? (son las tres opciones) Mi memoria RAM es de 512mb.
Gracias!!!

---

### Post by Mauro22 on 2007-08-30
Hace asi:

Borrá la swap y la ext3


Despues te creas una swap de unos 700mb.

Una particion / para el S.O, minimo 3 gb

Y, 

Si queres, podes crear una /home Sirve para guardas tus datos y configuraciones en una particion distinta a la del S. O en caso de reinstalar linux. El tamaño que quieras

Te va a quedar algo asi:

/dev/sda1 ntfs /media/sda1              235308mb desc
/dev/sda2 ext3 /                                ........mb .........mb
/dev/sda3 ext3 /home                       ........mb   .......mb
/dev/sda5 swap 700mb 0mb

---

### Post by FlyerDie on 2007-08-31
> **Mauro22 said:**
> 

Si queres, podes crear una /home Sirve para guardas tus datos y configuraciones en una particion distinta a la del S. O en caso de reinstalar linux. El tamaño que quieras


Ahi me hiciste acordar de porque crear una particion /home y no dejarla dentro de la particion de instalacion de linux :lolflag:

La duda que me surge al ver este thread es si no se puede instalar linux sin necesidad de volver a crear las particiones??
Osea, en el hipotetico caso de que suceda lo que le pasa a gakna...y quiera reinstalar pero no perder datos (teniendo solo particiones / y /swap) como deberia hacer? osea...para instalar sin borrar nada, solo pisando instalacion y no tocando archivos personales.

Saludos! :guitar:

---

### Post by marianom on 2007-08-31
> **FlyerDie said:**
> La duda que me surge al ver este thread es si no se puede instalar linux sin necesidad de volver a crear las particiones??
Osea, en el hipotetico caso de que suceda lo que le pasa a gakna...y quiera reinstalar pero no perder datos (teniendo solo particiones / y /swap) como deberia hacer? osea...para instalar sin borrar nada, solo pisando instalacion y no tocando archivos personales.

Saludos! :guitar:

Tenés que tener tu /home aparte. Para ello, y si ya tenes todo instalado y el /home es parte de la misma partición, podes usar [este HowTo]("http://www.psychocats.net/ubuntu/separatehome") para entender como separarlas con todo instalado.

---

### Post by gakna on 2007-09-01
Otra preguntita msangil...(me heché atrás en la reinstalación por este tema:): que pongo donde ofrece formatear cada una de las particiones, las marco a todas? a ninguna? a alguna??
Gracias!!!

---

### Post by Mauro22 on 2007-09-01
Podes formatear -o sea borrar todo- cualquier particion menos las que quieras dejar intactas, por ejemplo la de windows..


Si creas nuevas particiones, automaticamente se selecciona formatear.



Formatear = borrar todo

---

### Post by gakna on 2007-09-02
Ante todo muchísimas gracias por su paciencia y ayuda! pero lamentablemente creo que voy a desistir de Ubuntu, al menos por un tiempo...Resulta que reinstalé tal cual me explicaron, funcionaba todo bien, actualizé todo, bajé alguno que otro programa (gdesklets) y activé los efectos de escritorios que trae Feisty (las ventanas que se mueven y el cubo). Apagué la computadora y al volverla a prender...de nuevo la pantalla azul...no entra ni al login, ni nada, tengo que reiniciar. No se que habrá sido...los efectos talvez??
Lo que si les pediría es si saben como hacer que en el GRUB aparezca Windows primero así no tengo que elegirlo manualmente cada vez que inicio la computadora...
Saludos y gracias!

---

