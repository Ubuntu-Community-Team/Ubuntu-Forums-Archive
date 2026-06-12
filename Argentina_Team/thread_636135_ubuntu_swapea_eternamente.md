---
title: "ubuntu swapea eternamente"
date: 2007-12-09
forum: Argentina Team
---

### Post by ombzzz on 2007-12-09
hola gente

les hago una consulta, cada dos por tres en ubnutu  7.10 me pasa que empieza a trabajar el disco cada vez mas y a ponerse todo lento, hasta que la PC se vuelve "inusable" ( lo unico que hace es leer y leer a disco ) y no me queda otra que reiniciar

me imagino que debe tener algo que ver con que me quedo sin memoria y ubuntu empieza a swapear y a swaper sin descanso

lo que no entiendo bien es por que me pasa eso, siendo que:

i) tengo 512MB de memoria y particion de 1GB de swap

ii) no son muchas las aplicaciones que tengo cuando me pasa eso ( ej: firefox, openoffice y un par mas no muy grande )

y otra cosa que esperaria es que el kernel o el ubuntu me indiquen con algun mensaje de alerta  que tengo poca memoria o que el kernel no le esta dando el cuero para mantener estable el sistema ( en estos casos no me queda otra que reiniciar con el boton de la PC y pierdo todo lo que estaba haciendo ).

A alguien le pasa algo similar?

Googleando encontre recomendaciones como esta:

[http://www.guia-ubuntu.org/index.php?title=Minimizar_el_uso_del_swap](http://www.guia-ubuntu.org/index.php?title=Minimizar_el_uso_del_swap)

que indican parametrizar el kernel cambiando el % uso de swap ( disminuirlo )...

voy a probar con eso a ver si se soluciona el problema, si alguien me da alguna idea para entender por que me pasa eso y si hay alguna solucion se lo voy a agradecer

un saludo a todos

---

### Post by clasificado on 2007-12-09
Se me ocurre que tenes algun programa que se te está volviendo loco, consumiendo cada vez mas y mas memoria y por ende: swapea

Usala un rato, y cuando se ponga pesada, en una consola escribí
```
free -m
```

Eso te va a devolver algo asi:
```
              total         used         free       shared      buffers
  Mem:        14176        12592         1584            0         1440
 Swap:            0            0            0
Total:        14176        12592         1584
```

La linea que nos interesa es la última que dice cuanta memoria libre te queda (en megabytes).

En este caso, entre se ve que hay mucho USED y muy poco FREE, por lo que deberiamos de buscar cual es el proceso que se está llevando toda la memoria.

despues te digo como (cuando esté frente a un linux)

Clasificado

---

### Post by Federick on 2007-12-09
Hola.
Yo tuve esos problemas con el buscador de gutsy, el cual tuve que desinstalar completamente.
Buscá acerca de trackerd y fijate si corresponde con tu problema.
Saludos.

---

### Post by faktorqm on 2007-12-10
Hola muchachos, me sumo al post.

Les cuento mas o menos como es mi caso. Yo uso 7.04 todavia, tengo 512mb de ram y 2gb de swap. Ultimamente me paso mucho lo que se comenta aca, es mas, iba a abrir un post preguntando pero buenisimo, aprovecho este.
La cosa es que estoy trabajando lo mas normal del mundo en mi ubuntu, y de pronto pum! se me dispara el disco y empieza a trabajar a lo loco y no me deja hacer nada, y por ejemplo muevo el mouse y lo muestra con lag, saben que feo que es? parece que estuviera corriendo un scandisk en windows 98...... :@:@ (jajajajaj)
Yo primero pense que era el opera, asi que agarre y no lo use mas... pero volvio a ocurrir. Tenia enchufado un disco del laburo y ante la duda, lo desenchufe. 
Desenchufe camara digital, webcam y demas dispositivos usb. Sigue igual.
Yo la verdad, por suerte hasta ahora no me agarro nunca la loca de reiniciar, creo que una vez me calente no mas, pero lo dejas 15 minutos, media hora y para solo. 
Ahora, el problema es que vuelve!!!!!!!! capaz pasan 2 o 3 horas y de pronto... pum! luz roja permanente........ 
La verdad estoy re triste...... lo re quiero a mi ubuntu, pero necesito aprender mas sobre el y configurarlo a fondo..... por que asi esto no va. :( :(
le tire ahi en una terminal "ps ax" y lo unico raro que veo es que hay un proceso que se llama "pdflush", que aparece duplicado, y si intento cerrarlo, aparece triplicado, es decir, no se cierra el que queria cerrar, y aparece uno nuevo jajajajaj pobre ubuntu! anda a saber a donde le estoy metiendo el dedo xDxD
perdon por el post largo, pero es un problema de importancia. Despues les posteo mi "ps ax" comentando las cosas, por que me aparecen varias cosas duplicadas....
como hago para que me diga cuanta memoria consume cada proceso? o cuanto micro?
salu2 y gracias de antemano ^_^

---

### Post by kowal on 2007-12-10
Monitoreá con "top" (o htop) y "free -m" (como dijo clasificado) para ver cual es el programa/proceso que te está morfando la memoria.

---

### Post by faktorqm on 2007-12-10
Federick, me parece que diste en la tecla. Yo tenia instalado Beagle, al parecer, lo peor de lo peor cuando tenes 2 discos de 160gb y uno de 80gb............
puse top (kowal: sos un kpo!) y me tiraba el beagle-helper y otro mas, que habia instalado hace poco un coso que decia busqueda de escritorio. encima me acuerdo que lo instale por que me necesitaba buscar algo y me di cuenta que no habia un "buscar", y dije, como puede ser que estos tipos de linux no hayan hecho un "buscar" ½&/%@!@#~#~½ entonces me tope con ese beagle que decia que era bueno. estaba tan bueno que necesitaba mas hardware para correr!! ajajjajaj :P
bueno ok, no te puedo explicar lo que me acabas de ayudar man! no tenia ni idea de que pudiera ser ese el problema. gracias!!!!!!!!!!!!!!!!!!!!!!! ^_^

---

### Post by ombzzz on 2007-12-12
voy a intentar determinar el problema con "top" o "free" ... el problema es que cuando empieza a traquetear el disco no me deja ni siquiera abrir una terminal

cuando tenga tiempo pensaba hacer un script que escriba cada 5 seg en un log la salida del top para tratar de encontrar al culpable

espero sea un programa en particular ( le estoy sospechando al firefox porque me paso dos veces cuando entraba a la misma pagina )  y no algo del ubuntu o kernel, ya que no seria buena se#al que con 512MB me quede inusable la maquina tan facilmente

seria bueno que ubuntu "se de cuenta" de esta situacion ( veo que le pasa tambien a faktorqm ) y te de una opcion de parar la bocha con el programa que se esta comiendo la memoria o estabilizar la maquina 

igualmente, en window$ reiniciaba casi todos los dias porque se quedaba sin memoria ( me acuerdo que los iconos se empezaban a ver mail ) asi que agunate ubuntu ****** !

:)

---

### Post by faktorqm on 2007-12-13
guau! eso tendria que tener algo ubuntu. hay algunas paginas que tienen scripts que capaz te cuelgan el firefox. yo por eso uso el opera......... :KS o proba con el que te mas te guste. salu2!

---

