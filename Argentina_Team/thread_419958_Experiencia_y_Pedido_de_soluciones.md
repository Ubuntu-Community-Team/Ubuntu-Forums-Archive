---
title: "Experiencia y Pedido de soluciones"
date: 2007-04-23
forum: Argentina Team
---

### Post by lucianodato on 2007-04-23
Hola queridos ubunteros, mi nombre es Luciano, les queria contar de que soy nuevo en todo esto de linux-ubuntu, y que tras 1 mes de investigacion sobre este SO me decidí a bajarlo e instalarlo, y mas q nada porque ya estaba harto de mi buindows, espere ansiosamente a que saliera el "Feisty Fawn", lo descargue y grabe la imagen con el Nero. Antes de empezar a instalarlo, realice todos los pasos recomendados para mantener el doble booteo con buindows, ya que en mi familia son cabernicolas con la pc, a esto me refiero a los scandisk, las desfragmentaciones y backups. Primero probe el modo live y algunas veces me entraba y otras me tiraba errores, por lo q decidí hacer el test del cd en la pantalla de inicio, y me dio q estaba en correcto estado :) 

Listo me relaje entonces y comence la instalacion, cuando llegue a la parte de particiones le deje a linux el 20% de mi dico de 80gb, bien pase a la instalacion entonces, y cuando estaba por el 47% me dio errno 5, q segun dice es por qel cd esta mal grabado:confused: , y lo intente luego varias veces mas y no puede hacer nada, intente isntalarlo en modo seguro y avanzo un poco mas pero solo llego a el 57% :( , despues quise entrar al xp y me decia error loading operatong system, y muy astuto estube ya que antes me habia especializado en todo este tema por las dudas, bien ejecute los comandos fixboot y fixmrb desde el cd de l xp y nada, intente quitar las particiones ext3 y swap dejandolas como espacio libre y tampoco nada :mad:, en ese momento ya estaba loco, para colmo, lo tenia a mi hermano mas grande atras diciendome "dale dejame que quiero usar el messenger"  ](*,), bueno la custion es que alfinal tube que formatear todo el discoy crear particiones nuvas para instalar xp #-o.

Me puse a googlear acerca de este error y algunos recomendaban usar el cd de instalacion alternate, q me recomiendan que haga, no quiero mas windows, pero necesito el doble booteo si o si, por favor ayudenme porque realmente quiero introducirme en este so y esta comunidad...:(

Mi pc es la siguiente:

Atlhon 64 3500+
Motherboard Biostar TForce 6100 am2 (chipset nvidia 410)
Memoria ddr2 667mhz 1024 novatech (apoyando lo nacional)
Disco rigido hitachi SATA2 80gb
Lecto grabadora de DVD LiteOn

---

### Post by jayflower on 2007-04-23
Como hiciste las particiones ? cuando instalaste XP? lo más simple es dejar espacio libre sin particionar en los ultimos cilindoros del disco para que Linux los maneje solo. Eso lo hacés cuando instalas Windows.Si contás bien que hiciste tal vez te podemos ayudar. A mi me pasó algo parecido

---

### Post by lucianodato on 2007-04-23
jajaja, para colmo esa fue mi primera experiencia formateando xp, no me resulto dificil, pero quizas hice algun paso mal, q no me llamaria la atencion.

Lo que ralice fue lo siuguiente, en la instalacion de buindows, borre todas las particiones, luego cree una nueva, pero me dejo 8 mb en espacio libre, quizas a lo que te referis es a eso, q no tendria q haber hecho esa particion, seguro q es eso :), ya q era la primera ves no lo sabia, todo esto lo hice despues de ver q me fallaba el ubuntu, no antes de la instalacion, se entiende no?, o sea q ahora tengo el xp instalado en la particion q cree y me quedan esos 8mb de espacio libre (q burro q soy)...:(

---

### Post by jayflower on 2007-04-23
que tamaño tiene el disco? cuanto tiene asignado a Windows? 8MB es muy poco:? o serán 8 GB ? el asunto es... cuando se instala por primera XP se pueden borrar todas las particiones y volverlas a generar, utilizando un porcentaje del total y dejando el resto para lo que sea, ese ultimo resto yo lo dejaría para Ubuntu, con resto no quiero decir que sea un poquito, solo que sea todo el espacio libre al final.

---

### Post by sebas.rhcp on 2007-04-23
Yo me mande como rambo e instale Ubuntu 6.10 en la particion del Windows XP, adios Windows. Ubuntu me tomo las particiones NTFS en modo lectura lo cual era suficiente para acceder a los drivers necesarios el modem usb y asi levantar internet y actualizar. Cuando salio Feisty lo unico que hice actualizar la distribucion y ahora tengo Feisty andando con compiz.

---

### Post by lucianodato on 2007-04-24
ah listo entonces, lo q puedo hacer es, hacer una particion de 60gb para windows y dejar 20 de espacio libre para q despues el gpated pueda utilizarlo para alojar el linux...seria esto correcto?

otra pregunta...me conviene grabar la imagen con el nero o con el ashampoo burning studio?

Saludos

---

### Post by screening on 2007-04-24
mmmm eso de los 8 megas es un error del particionador del xp, lo he visto muchas veces, te deja reservado ese espacio y no se para que, lo que te conviene hacer es formatear el rigido con alguna utilidad para ello antes de empezar a instalar xp. Muchas veces uso Hiren's Boot Cd o sino   directamente con Partition Magic.

Dependiendo de la memoria ram que tengas tenes que asignar el espacio para la swap de ubuntu, (es una particion mas)

Para que tengas una idea te muestro mi configuracion:
Tengo un rigido de 200 gigas con 1 giga de ram en mi pc.
Como instale Vista (no se para que, ni lo uso) particioné en 4 asi:

1º) 100 gigas: Vista
2º) 20 Gigas: Feisty, fichero raíz /
3º) 512 megas: la swap de linux (porque tengo un giga de ram no necesito tanta swap, ojo)
4º) 79,4 gigas para mi /home

---

### Post by felipelerena on 2007-04-24
Luciano, no se si fu un typo o no, pero te corrijo por las dudas, es "gparted" en vez de "gpated"
lo del error del cd tenes una manera de chequearlo, el mismo cd viene con un sitema para chequear la integridad... por ahi bajaste mal la imagen

---

### Post by lucianodato on 2007-04-24
Si disculpas escribi mal... La integridad del cd la verifique y me dio q estaba todo correcto...por eso es mi inconveniente, y problemas de incompatibilidad no creo tener porque el modo live me funcionaba correctamente (algunas veces no entraba y otras si), el tema radica, en mi opinion, a que la imagen la grabe con el nero, y he leido que el nero siempre presenta problemas al grabar la imagen...

Quizas lo q deberia hacer es, formatear todo e instalar primero el xp en una particion que ocupe solo 60gb y el resto dejarlo libre, (es decir sin particionar), para que cuando corra el programa de instalacion de linux, en el gparted elija la opcion de utilizar el espacio libre disponible, que como tengo un disco rigido de 80, serian 20gb, y el programa se encargaria solo de crear la particion ext3 y la swap...

Y si no lo puedo solucionar asi, deberia ser q la imagen que descargue es erronea..

Si alguien me puede dar algun consejo se lo agradeceria...

---

### Post by Illuminator on 2007-04-24
Hola luciano y toda la comunidad ubuntera. Yo también soy un usuario prácticamente inexperto, sin embargo pude bajar e instalar sin problemas Feisty, incluso configure la placa 3d, internet y tengo funcionando Beryl. Lo que hice fue básicamente desfragmentar la particion donde tenia window$ (estaba solo en todo el disco), luego antes de grabar la imagen .iso en un CD-RW (con Nero 6.6.0.8 ) comprobe que conincidiera el md5sum de la imagen con la que aparecia en la web (como hacer esto: [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)), al asegurarme de que coincidian recien ahi grabe el disco, fijate que quizas sea ese el problema del cd mal grabado.

Saludos.

---

### Post by Al_maverick on 2007-04-24
Yo probaría hacer la instalacion esta vez usando el alternate CD en vez del desktop. Si bien es en modo texto, y no tan "linda" como la instalacion grafica, en mi experiencia es mucho mas confiable. 
Las preguntas para la instalacion no son tantas y estan bien explicadas.

---

### Post by jpmorelli on 2007-04-24
Tu problema original me suena mas a que tu Lecto-grabadora tiene errores erráticos de lectura y/o escritura, tal vez tuviste la mala suerte de que justo pasó cuando estabas instalando... por lo de las particiones, cuando tuve ese problema ejecuté como dijiste FIXBOOT, FIXMBR y levantó como si nunca hubiera pasado nada, lo que no recuerdo es si no le hice un Sys C: nuevamente pero bueno, esperemos que no te vuelva a suceder, te aseguro que no te vas a arrepentir cuando tengas instalado Feisty :) 
Suerte !

---

### Post by lucianodato on 2007-04-25
Bueno Gracias, lo antes que pueda pruebo todo y les comento como me fue, igualmente por las dudas voy a usar el ashampoo burning studio para grabar el cd (me gusta mas que el nero :) )

---

