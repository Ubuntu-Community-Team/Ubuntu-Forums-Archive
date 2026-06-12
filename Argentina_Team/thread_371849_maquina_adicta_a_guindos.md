---
title: "maquina adicta a guindos"
date: 2007-02-27
forum: Argentina Team
---

### Post by fetova on 2007-02-27
hola, hago este post debido a que estoy harto de usar ubuntu en la maquina de mi trabajo asi!!!!:mad: :mad: :mad: :mad: 

No se que sucede, uso el liveCD, Ubuntu corre bien al principio y despues se alenta, Xubuntu desde el inicio esta lenta, ayudaa!!![-o< [-o< 

No se que datos dar para que me ayuden, asi que diganme por favor que seria necesario.

Gracias:)

---

### Post by spg76 on 2007-02-27
¿Cuanta memoria RAM tiene la máquina? Porque si tenes 256 o menos te va a funcionar bastante lento.
Por otro lado, ¿no podes instalarlo en una partición del disco rígido? La diferencia de rendimiento entre LiveCD y HD es muchisima.

---

### Post by clasificado on 2007-02-27
¿Que clase de programas usas? ¿Cuanto tiempo la aguantas antes de que se ponga insoportable?

cuando la cosa se ponga pesada, ejecutá el comando **free** en una consola. Te devuelve en numeros el estado de tu memoria, Pasalo por acá y te decimos que tan mal está 	:D

Clasificado.

---

### Post by Nemesis Teufel on 2007-02-28
> **clasificado said:**
> 
Pasalo por acá y te decimos que tan mal está 	:D

Aca esta el mio pa ver q tan mal ando..
> 
                    total         used       free     shared    buffers     cached
Mem:        515936     504452      11484          0      33976     129904
-/+ buffers/cache:     340572     175364
Swap:      1052216      38256    1013960


Tengo otro usuario corriendo, pero no deberia tener mas swap usado en vez d tanta memoria?

---

### Post by clasificado on 2007-02-28
> **Nemesis Teufel said:**
> Aca esta el mio pa ver q tan mal ando..

Tengo otro usuario corriendo, pero no deberia tener mas swap usado en vez d tanta memoria?

Respuesta Rápida: **Ubuntu prefiere usar primero toda la memoria física**. ¿Para que va a realentizar la maquinola usando el disco si todavia tiene memoria disponible? Aunque esto es recomendable para equipos con 512 para arriba; Si se tiene menos se llena rápido con las cosas de sistema y termina usando todo el tiempo el disco para todo lo del usuario.

para ver que criterio usa tu ubuntu, usá **sudo cat /proc/sys/vm/swappiness**. Para cambiarlo, [por acá hay un thread que habla del asunto, escondido bajo --Swap--]("http://www.espaciolinux.com/foros-tema-p86441.html")

Por otra parte, La linea que un usuario común debe leer del comando free es esta:
```

-/+ buffers/cache: 340572 175364

```
Que dice claramente 332mb usados, 171mb libre. En mi humilde opinion, no está mal :)

Para verlo en MB directamente, agregale al comando free la opcion **-m**.

---

### Post by fetova on 2007-02-28
quisiera instalarlo ahi, pero no se va a poder hasta el proximo año, la buena noticia es que no solo seria la laptop, sino todas las computadoras de mi chamba :) mi jefa vio beryl y se enamoro de el.

Pero retornando a mi maquina puse el archivo y ahorita estoy trabajando desde otra maquina pues me volaron la lap, quien sabe quien la tiene, pero checo en cuanto la devuelvan.

los programas que uso cuando se me traba es Rhythmbox, firefox, gaim, y openoffice.org writer.

---

### Post by fetova on 2007-02-28
ubuntu@ubuntu:~$ free
                 total           used           free         shared        buffers         cached
Mem:             507240         500724           6516              0          20368         253604
-/+ buffers/cache:         226752         280488 
Swap:                0              0              0
ubuntu@ubuntu:~$ 

Programas firefox (viendo este post) , navegador de archivos (el la unidad usbdisk), terminal, gaim (iniciado por primera vez), añadir y quitat aplicaciones (Gstreamer plugins (los codecs de mp3, wma...))aqui se ralentizo en el momento en el que le di OK para instalar.

aparte en el arranque aparece [17179713.712000]ali15x3_smbus (no se que mas)que actualize el bios o use force_addr=0xaddr, esto lo use y de todos modos estoy escribiendo de una manera predictiva y bastante molesta este post :mad: 

si se necesita algo mas me dicen
Muchas gracias

---

### Post by fetova on 2007-03-02
Hola...

se podria que me ayuden?

Necesito poner mas info?

gracias

---

### Post by beuno on 2007-03-02
> **fetova said:**
> hola, hago este post debido a que estoy harto de usar ubuntu en la maquina de mi trabajo asi!!!!:mad: :mad: :mad: :mad: 

No se que sucede, uso el liveCD, Ubuntu corre bien al principio y despues se alenta, Xubuntu desde el inicio esta lenta, ayudaa!!![-o< [-o< 

No se que datos dar para que me ayuden, asi que diganme por favor que seria necesario.

Gracias:)

¿Estas laburando DESDE el livecd?

Si es asi, te diria que no es una opcion, tiene que estar constantemente yendo a leer el CD.
No va a funcionar nunca suficientemente bien.

---

### Post by fetova on 2007-03-02
> **beuno said:**
> ¿Estas laburando DESDE el livecd?

Si es asi, te diria que no es una opcion, tiene que estar constantemente yendo a leer el CD.
No va a funcionar nunca suficientemente bien.

mmmmm

si ahorita es asi, pero tambien, por cierto, tambien me paso que aun teniendolo instalado, eso pasaba en esta maquina, de hecho, una vez que me paso y me sentia harto, hice un bug en launchpad porque no solo fue la lentitud, tambien me cerro firefox, por cierto, tenia el estado de "needs info", pero cuando me llego la notificacion, y habia tenido que quitar y volver a win :(

---

### Post by beuno on 2007-03-02
> **fetova said:**
> mmmmm

si ahorita es asi, pero tambien, por cierto, tambien me paso que aun teniendolo instalado, eso pasaba en esta maquina, de hecho, una vez que me paso y me sentia harto, hice un bug en launchpad porque no solo fue la lentitud, tambien me cerro firefox, por cierto, tenia el estado de "needs info", pero cuando me llego la notificacion, y habia tenido que quitar y volver a win :(

Olvidate de usarlo a una velocidad razonable desde el LiveCD.
Ahora, una vez instalado, con 512 de RAM (que es lo que pareces tener), tiene que funcionar sin problemas.

Despues nos contaras   :D

---

### Post by fetova on 2007-03-02
> **beuno said:**
> Olvidate de usarlo a una velocidad razonable desde el LiveCD.
Ahora, una vez instalado, con 512 de RAM (que es lo que pareces tener), tiene que funcionar sin problemas.

Despues nos contaras   :D

ya lo he tenido instalado en la maquina, aguanta unos pocos programas mas (2) y pasa lo mismo:( reinstale como 3 veces, ahora se que no debi hacer eso, no era necesario, pero bueno...

alguna idea de que podria hacer?

---

### Post by jpmorelli on 2007-03-04
Evidentemente alguno de los dispositivos de hardware no es "totalmente" compatible con Ubuntu y te está causando esa gran inestabilidad en el sistema.
Hay que empezar a buscar descartando de a poco e ir encerrando ( o aislando el problema ).
PAra empezar una pregunta... tenés por casualidad algun modem de esos que vienen con el motherboard ya incorporado ? Un AMR o algo parecido ?, Generalmente causan grandes dolores de cabeza...

---

### Post by fetova on 2007-03-05
> **jmorelli said:**
> Evidentemente alguno de los dispositivos de hardware no es "totalmente" compatible con Ubuntu y te está causando esa gran inestabilidad en el sistema.
Hay que empezar a buscar descartando de a poco e ir encerrando ( o aislando el problema ).
PAra empezar una pregunta... tenés por casualidad algun modem de esos que vienen con el motherboard ya incorporado ? Un AMR o algo parecido ?, Generalmente causan grandes dolores de cabeza...

ya vi que sucede... se necesita actualizar el BIOS, el unico problema :popcorn: es que es PC portátil Compaq Presario 2105LA, ahora, el articulo que encontre es este: [http://h10025.www1.hp.com/ewfrf/wc/document?docname=c00374655&cc=es&lc=es&dlc=es&product=430187&dlc=es&lang=es]("http://h10025.www1.hp.com/ewfrf/wc/document?docname=c00374655&cc=es&lc=es&dlc=es&product=430187&dlc=es&lang=es")
ahi viene para descargar cuatro imagenes que se pueden usar para actualizar el BIOS **QUE NO SON el modelo** :mad: 

alguno servira?

---

