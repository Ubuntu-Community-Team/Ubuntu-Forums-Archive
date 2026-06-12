---
title: "Ayuda a un principiante"
date: 2008-03-09
forum: Argentina Team
---

### Post by dariofal on 2008-03-09
Hola !

Soy bien nuevito en esto de Linux, es más, apenas tengo el Live CD de Ubuntu 7.10.

Mi situación es la siguiente:

PC 1 
PIII - 800 Mhz 
512 Mb RAM
Disco de 30 Gb Con 2 particiones: 
C: 15 Gb (con XP) - 7,5 Gb libres
D: 15 Gb (documentos personales) - 11 Gb libres

PC 2
P IV - 2.8 Ghz
2 Gb RAM
Disco de 80 Gb con 2 particiones: 
C: 40 Gb (con XP) - 22 Gb libres
E: 40 Gb (documentos personales) - 17 Gb libres

La idea es instalar Ubuntu primero en el PC 1 (PIII que es el que uso para la administración y no es tan importante), para irme familiarizando con el y más adelante instalarlo en el PC 2 (P IV) que es en el que trabajo todos los días.
En ambos casos me gustaría mantener el XP, o sea que debería poder optar con que sistema arrancar.

He leido testimonios de algunos usuarios que han tenido problemas en la instalación o con la detección de hardware, drivers, etc. y me surgen varias dudas.

Alguien me podría orientar acerca de cuales son las posibilidades de instalarlo en uno u otro PC ?

Desde ya muchas gracias.

---

### Post by tzulberti on 2008-03-09
Para ver si todo tu hardware va a ser detectado es simple: mete el livecd, y fijate si todo funciona correctamente. Lo que no te funcione en el livecd es con lo que vas a tener problemas mas adelante. Para un poco mas de detalles, el proceso de instalacion es asi: metes el LiveCD, y luego de que te carga automaticamente la pantalla grafica (lease Gnome, Kde o Xfce), en el escritorio te aparece un icono de Instalar. Por eso, cuando se cargo la pantalla grafica todo tu hardware ya tendria que haber sido detectado. Si apagas la maquina (tiene una opcion para apagar la maquina correctamente) no va a cambiar nada en tu PC, por lo que lo podes probar cuantas veces quieras.

Sobre que instalar: en la P3, talvez no te convenga Ubuntu, pero si Xubuntu porque es para maquinas mas viejas.

---

### Post by dariofal on 2008-03-09
Antes que nada, gracias por responder.

Listo, ya estoy bajando Xubuntu para la PIII.

Que opinas sobre el tema de las particiones ?

Dónde me conviene instalar ?

Sabes de algun sitio que contenga algún tutorial o información más detallada al respecto ?

Gracias una vez más.

---

### Post by Radiobuzz on 2008-03-09
Hola Darío, 

Hay un programa llamado Wubi que puede servirte: [http://wubi-installer.org/](http://wubi-installer.org/)
El problema es que sólo funciona con Ubuntu 7.04 (la anteúltima versión), pero en todo caso después de instalar podés actualizar desde el SO mismo. Lo que hace ese programa es instalarte Ubuntu en un disco rígido virtual que está adentro de la partición de Windows y luego te reescribe el boot.ini para que puedas bootear con uno u otro SO. Está bueno porque te ahorrás el tema de particionar el disco, aunque a mí en particular no me atrae mucho la idea de tener un disco virtual. En todo caso hay un tutorial por ahí bastante simple para mover los datos desde ahí a una partición dedicada. Ojo, para usar Wubi necesitás la imagen de Ubuntu 7.04 alternate CD, que si no lo tenés lo baja el programa mismo.

Si lo que querés es particionar el disco e instalarlo ahí, necesitás una partición para el sistema (como mínimo unos 8 GB), otra para el SWAP (1 GB está bien) y yo te recomiendo una tercera donde poner tu carpeta personal. Si no me equivoco, esto se puede hacer desde el propio instalador de Ubuntu aunque no estoy muy seguro.

---

### Post by pante on 2008-03-09
Tengo un PIII y la velocidad de la CPU no es tan limitante como la memoria. Con 512 MB de RAM Ubuntu te debería andar perfectamente. Tengo instalado Ubuntu en un PIII con 635 MB de memoria y corre como una gacela :)

Pero no se pierde nada con probar.

Saludos

---

### Post by dariofal on 2008-03-10
A ver si entiendo.

Ya tengo un disco con 2 particiones:

Disco de 30 Gb Con 2 particiones:
C: 15 Gb (con XP) - 7,5 Gb libres
D: 15 Gb (documentos personales) - 11 Gb libres

Dicen que debería crear otras 3 particiones, una para Ubuntu, otra swap y otra para mis cosas. Es así ?

Disculpen mi torpesa si es que no lo entiendo, pero lo cierto es que mis máqiunas son al mismo tiempo herramientas con las que trabajo todo los días y me generaría muchos contratiempos errarle en esto por no preguntar o entender mal.

Gracias una vez más.

---

### Post by Tosh78 on 2008-03-10
Hola Dario! Como estas? Yo tambien te recomiendo que intentes primero con Wubi, aunque te cuento que si existe para la version 7.10
De hecho aca te explica de donde bajar cada cosa y como hacerlo: [https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)
Yo empece asi. Lo probe con wubi, vi que me reconocia todo y despues lo instale bien. Ojo. Lo tuve como 2 semanas con wubi para probarlo a full y la verdad es que me sorprendio lo bien que anduvo. En mi opinion, no creo que vayas a tener problemas de hardware, ya que la version 7.10 al menos, esta muy bien. Yo no tuve ningun problema y eso que tengo una laptop.
Yo creo que antes de que particiones podes desfragmentar el disco y usar el wubi. Ahi ves como funciona, si te reconoce todo bien, lo probas a full y si todo va bien, lo instalas. Si vez que hay algun problema, vas al panel de control de wingarch y lo sacas con Agregar/Quitar programas.
Si tenes alguna duda con Wubi, podes escribirme por mensaje privado, que voy a intentar ayudarte en lo que pueda.

---

### Post by felipelerena on 2008-03-10
Dario, no quiero asustarte ni nada, pero si la maquina la usas para laburar te recomiendo hacer un backup de todos los datos sensibles...
Saludos,
Lipe

---

### Post by andy_91 on 2008-03-10
> **dariofal said:**
> A ver si entiendo.

Ya tengo un disco con 2 particiones:

Disco de 30 Gb Con 2 particiones:
C: 15 Gb (con XP) - 7,5 Gb libres
D: 15 Gb (documentos personales) - 11 Gb libres

Dicen que debería crear otras 3 particiones, una para Ubuntu, otra swap y otra para mis cosas. Es así ?

Disculpen mi torpesa si es que no lo entiendo, pero lo cierto es que mis máqiunas son al mismo tiempo herramientas con las que trabajo todo los días y me generaría muchos contratiempos errarle en esto por no preguntar o entender mal.

Gracias una vez más.

mira lo que quiso decir creo que fue esto

1.una partición de 10gb para xp(yo te recomiendo 10 así no te falta lugar luego para las otras particiones)
2-una partición fat32 de 10gb para tener los documentos y usarla de intercambio
3-una partición de 1gb(pero yo te recomiendo 2) para swap y lel resto del disco en otra partición para instalar el Xubuntu

a mi siempre me detecto automático el booteo pero yo siempre lo use con win2k

los problemas que tuve fueron con la impresora(tuve es pasado:P los tengo :p)

en cuanto a Xubuntu yo lo tuve y te puedo dar una mano

otra distro muy bueno para los novatos es urli basada en kubuntu

para mas información ingresa al google......

después de instalado te recomiendo amarok como reproductor de musica y totem como reproductor de vídeo(totem viene incluido en Xubuntu)

como navegador web el firefox que también viene incluido

como mensajero instantáneo de la red msn te recomiendo emesene que también viene para windows, siempre y cuando no uses webcam si usas webcam te recomiendo amsn

el visor de fax de windows lo reemplazas por el eog(eye of gnome) que no viene en Xubuntu pero esta en los repositorios

gnumeric y open office hojas de calculo reemplazan sin problemas a exel, con la diferencia que gnumeric consume menos recursos

a el ares lo reemplazas bien con limewire o frostwire

para instalar programas en Linux también tenes ejecutables y además los repositorios oficiales

bueno por ahora es lo que se me ocurre cualquier cosa fíjate que en mis post hay un par (por no decir muchas) preguntas básicas de donde podes sacar las respuestas que me dieron

tal vez te alguna te ayude


espero haberte ayudado

---

### Post by dariofal on 2008-03-11
Ahhh

Gracias por la aclaración...!
Doy por sentado que el tema de las particiones lo resuleven sin problemas tanto Ubuntu como Xubuntu verdad ?
El partition Magic no lo quiero ver ni en figuritas, ya tuve una mala experiencia con él...probablemente yo cometí el error....pero viste com es esto: "el que se quema con leche, ve la vaca y llora !" jeje

De cualquier manera todavía tengo que respaldar todo antes de entrarle así que GRACIAS a todos !

---

### Post by andy_91 on 2008-03-11
> **dariofal said:**
> Ahhh

Gracias por la aclaración...!
Doy por sentado que el tema de las particiones lo resuleven sin problemas tanto Ubuntu como Xubuntu verdad ?
El partition Magic no lo quiero ver ni en figuritas, ya tuve una mala experiencia con él...probablemente yo cometí el error....pero viste com es esto: "el que se quema con leche, ve la vaca y llora !" jeje

De cualquier manera todavía tengo que respaldar todo antes de entrarle así que GRACIAS a todos !
si el tema de las paticiones nose si se puede achicar la de xp nunca probe pero creo que si para lo demas al instalar el asistente te da la opcion de gestionar las particiones:

te da estas opciones
automatico(usando espacio libre en el disco)

automatico(usando todo el disco)

manual(ese es la que tenes que elegir)

el asistente de instalacion es el mismo para ubuntu y Xubuntu

---

