---
title: "Ubuntu 8.04 en una AMD: Ayuda en la Instalacion."
date: 2008-04-27
forum: Argentina Team
---

### Post by mari_ on 2008-04-27
Hola, acabo de comprarme una cpu nueva, procesador Athlon 64 dual core 5200, mother msi k9n6sgm-v, 1 gb ddrII, rigido 160 gb serial attaII.
Intente arrancar el live cd de ubuntu 8.04-desktop-amd 64, pero luego de cargarse la barra de ubuntu aparece: ubuntu@ubuntu~$: _
y no se que tengo que poner! 
Les agradeceria me dijeran que comando debo ingresar para continuar el proceso y ejecutar el live cd. Mi intención es instalarlo, pero  no quiero ejecutar esa opcion directamente por miedo :( (es mi primera vez con linux)
espero ayuda, gracias...

---

### Post by GepettoBR on 2008-04-27
desculpame se mi español no es el mejor....

Lo que el LiveCD está haciendo es logar en una sessión CLI, es decir, sin la interface gráfica. Puede haver un problema con su videoboard.Tenta ejecutar el comando ```
startx
```

---

### Post by User21 on 2008-04-27
mari_:Siendo tu primera vez en Linux, yo te recomendaría usar la versión de 32 bits. Al iniciar el CD, elige de entre las opciones de abajo, el modo VGA, asi puedes tener video seguro, o busca una opcion que diga modo grafico seguro. Sigue preguntando que aqui estaremos.

---

### Post by valucha on 2008-04-27
[COLOR="DarkOrchid"]Mari, yo tengo una compu con similares características a las tuyas y uso Ubuntu 32bits...
La verdad que vuela y no hace falta ponerle Ubuntu 64 bits para que vyaa más rápido, más por el hecho de que casi no hay ningún programa para esa plataforma y vas a tener problemas con TODO (al igual que WIndows, por ejemplo, no vas a poder instalar el flash en Firefox, es decir, no vas a poder ver videos de Youtube ni nada de eso). 

La realidad es que si sos experto y sabés lidiar con los problemas que eso conlleva adelante!! estarías aportando un montón a la comunidad...
Pero para novatos como nosotros (yo llevo 2 años en Linux, aprendiendo, leyendo, y demás y aún me considero novata, al menos para eso) es mejor usar la comunacha, que todo el mundo tenga y  te puedan ayudar si llega  a ocurrir algún problema, o si simplemente quieres instalar más programas que los que vienen por defecto...


Saludos, y ojalá te sirva mi opinión.[/COLOR]

---

### Post by mari_ on 2008-04-28
Hola, gracias por responder, otra pregunta:
La version 32 bits es la i386 ?
pregunto porque antes de instalar la version 64 bits intenté instalar ubuntu 7.10 i386, y al llegar a la parte de comprobación de audio y sonido(al inicio, apenas arranca ubuntu) el monitor mostraba toda una imagen desfigurada, con rayas, como si estubiese roto! 
Al no saber solucionar ese problema, cambie de live cd, y elegi la version 64 bits.
La version 32 bits es la i386 ? que hago?

---

### Post by faktorqm on 2008-04-28
Si, la version de 32 bits es la i386. Para que no te muestre eso, en la primer pantalla del live cd elegi el modo de compatibilidad VGA o algo relacionado con VGA en el menu. Asi de ultima te arranca en 640x480 o en 800x600 y no tenes ningun 0problema. Salu2!

---

### Post by valucha on 2008-04-28
> **mari_ said:**
> Hola, gracias por responder, otra pregunta:
La version 32 bits es la i386 ?
pregunto porque antes de instalar la version 64 bits intenté instalar ubuntu 7.10 i386, y al llegar a la parte de comprobación de audio y sonido(al inicio, apenas arranca ubuntu) e**l monitor mostraba toda una imagen desfigurada, con rayas, como si estubiese roto! **
Al no saber solucionar ese problema, cambie de live cd, y elegi la version 64 bits.
La version 32 bits es la i386 ? que hago?
[COLOR="DarkOrchid"]
Yo tengo una nvidia 7300 y también me pasa con el live cd, es cuestión de esperar unos segundos después inicia normalmente y podés probar el live cd y si te gusta instalarlo. Una vez instalado no tenés más ese problema.


Si no tenés la misma placa de video, sé que pasa con bastantes Nvidia gforce, y con una intel de laptoc también me pasó...

Suerte :)
[/COLOR]

---

### Post by mari_ on 2008-04-28
> **valucha said:**
> [COLOR="DarkOrchid"]
Yo tengo una nvidia 7300 y también me pasa con el live cd, es cuestión de esperar unos segundos después inicia normalmente y podés probar el live cd y si te gusta instalarlo. Una vez instalado no tenés más ese problema.


Si no tenés la misma placa de video, sé que pasa con bastantes Nvidia gforce, y con una intel de laptoc también me pasó...

Suerte :)
[/COLOR]

Hola, esperé un rato y nada seguia igual, si se observa con cuidado se ve a lo ancho de la pantalla, en el centro, la flechita del mouse, se puede mover y todo, pero esta totalmente distorsionada la imagen!
No se que hacer, use el live cd i386 y probé cambiando la resolucion a 800 x 600 como dijeron, pero el problema persistió :(
que me aconsejan hacer?

---

### Post by faktorqm on 2008-04-28
Tenes que instalar el ubuntu con un cd que se llama "alternate" que viene de alternativo. Cuando no podes correr la interfaz grafica para realizar la instalacion, el cd alternativo te permite hacerla a través de modo texto. No te asustes, es la misma instalacion que ibas a hacer en modo grafico, pero en modo texto. Las opciones son las mismas, y eso te va a permitir arrancar el instalador, y luego el sistema equivalentemente al instalador grafico.
Para bajarlo, vas donde fuiste a bajar el ubuntu i386 antes solo que abajo del boton de download hay una casillita que te dice, que si queres el alternate cd la marques. Marcala y bajalo.
Suerte y saludos, si tenes dudas no dudes en preguntar. Salu2!!

---

### Post by Mauro22 on 2008-04-28
Cuando carga el cd en el menu de ubuntu. Apreta F4 creo que es la opcion de Modos. Y elegi a pruebas de fallos y despues le das a la opcion de probar ubuntu o instalar!!

:guitar:

---

### Post by mari_ on 2008-04-28
> **faktorqm said:**
> Tenes que instalar el ubuntu con un cd que se llama "alternate" que viene de alternativo. Cuando no podes correr la interfaz grafica para realizar la instalacion, el cd alternativo te permite hacerla a través de modo texto. No te asustes, es la misma instalacion que ibas a hacer en modo grafico, pero en modo texto. Las opciones son las mismas, y eso te va a permitir arrancar el instalador, y luego el sistema equivalentemente al instalador grafico.
Para bajarlo, vas donde fuiste a bajar el ubuntu i386 antes solo que abajo del boton de download hay una casillita que te dice, que si queres el alternate cd la marques. Marcala y bajalo.
Suerte y saludos, si tenes dudas no dudes en preguntar. Salu2!!

Bueno, ahora pongo a descargar el alternativo, y sin dudas te vuelvo a consultar;), cualquier minimo problema es un gran problema para mi,jaja.
gracias a todos por responder, mañana los vuelvo a molestar :)

---

### Post by mari_ on 2008-04-29
Hola, me preguntaba como hacer con el tema de las particiones.
Yo tengo win xp en una particion C (70 GB) y tengo otra particion para archivos y esas cosas D (80 GB).
Debo hacer mas particiones? con esas dos me alcanza? donde debo instalar ubuntu?

---

### Post by sajnox on 2008-04-29
Si, basicamente necesitas hacer una particion mas que es la que aloja el sistema (en realidad vas a hacer otra mas para el swap pero esa te la hace automaticamente el instalador, por el momento no te compliques mas de lo necesario. Nada de lo que hagas en la instalacion es definitivo)

Para mas datos de la instalacion te recomiendo que visites la guia ubuntu: [www.gui-ubuntu.org](www.gui-ubuntu.org)

---

