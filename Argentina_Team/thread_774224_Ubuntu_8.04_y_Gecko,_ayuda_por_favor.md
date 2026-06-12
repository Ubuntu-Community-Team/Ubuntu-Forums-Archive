---
title: "Ubuntu 8.04 y Gecko, ayuda por favor"
date: 2008-04-29
forum: Argentina Team
---

### Post by smrdelj on 2008-04-29
Hola buenos dias. Soy bastante nuevo en Ubuntu y tambien en el foro.

Quisiera pedirles ayuda con un asunto que me está volviendo loco:

Resulta que quiero instalar Steam. Luego de mucha lucha, logré instalar wine y hacerlo correr (esto fue realmente un logro. La verdad q el wine no se cansaba de arrojarme incompatibilidades). Luego instalé Steam. El problema es que, al loguearme a mi cuenta, en vez de entrar a Steam se me cierra todo. Es decir, que en el momento en q Steam deberia desplegarse, se cierra.

Encontré que esto se debe al Gecko, ya que debe estar instalado.

Y acá está el problema. He intentado por lo menos 5 maneras distintas postuladas en diferentes guias y foros y nada ha resultado. Sobre todo, hay algo que me llama la atencion: en todos los foros dicen que wine deberia automaticamente preguntarte si deseas instalar Gecko (cosa de la q puedo dar fe en ubuntu 7.10); pero esto a mi no me sucede (osea, en 8.04 no te pregunta nada, directamente se cierra Steam).

Es todo esto problema de compatibilidad con Ubuntu 8.04?

Alguien por favor me puede ayudar a instalar Gecko para correr Steam?

Muchas gracias, saludos

EDIT: este dato quiza pueda servir: cuando ejecuto en Terminal este comando (wine iexplore [http://winehq.org](http://winehq.org)), me salta una ventana titulada "Wine Internet Explorer" que dice "El renderizado HTML está actualmente deshabilitado"

---

### Post by smrdelj on 2008-04-29
Disculpen que haga esto, pero mi thread ya pasó a la segunda pagina y nadie pudo ayudarme.

Posteo para darle un refresh y que vuelva al listado principal :S

Sigo atento esperando ayuda.

Muchas gracias, disculpen mi conducta. Saludos

---

### Post by faktorqm on 2008-04-30
Mal, muy mal. Aca la gente siempre lee todos los foros.
Tiron de orejas :D

aca te explican todo:

[http://www.tuxapuntes.com/tux/content/view/789/44/](http://www.tuxapuntes.com/tux/content/view/789/44/)

Si ya lo viste y no te anduvo comenta. Salu2!!

---

### Post by smrdelj on 2008-04-30
Hola que tal. Muchas gracias por responder. Disculpen mi refresh post :$

Sigo sin poder hacer nada con el Gecko :(

Como dije anteriormente, cuando ejecuto en Terminal el comando "**wine iexplore [http://winehq.org](http://winehq.org)**" (mediante el cual se instala Gecko), me salta una ventana titulada "Wine Internet Explorer" que dice "**El renderizado HTML está actualmente deshabilitado**"

Qué debo hacer? Muchas gracias

---

### Post by euzkoarima on 2008-04-30
Ni idea de que es el steam, pero busqué y encontré [esto]("http://ubuntuforums.org/archive/index.php/t-47169.html") que quizás te sirva. En particular fijate al final, que dice que es un problema de fonts (Tahoma).

Suerte.

---

### Post by marianom on 2008-04-30
> **smrdelj said:**
> Disculpen que haga esto, pero mi thread ya pasó a la segunda pagina y nadie pudo ayudarme.

Posteo para darle un refresh y que vuelva al listado principal :S

Sigo atento esperando ayuda.

Muchas gracias, disculpen mi conducta. Saludos

No tiene nada de malo, después de un tiempo prudencial es correcto hacerlo si no has recibido ayuda (en lenguaje forero se llama "bump" y generalmente solo se escribe esa palabra).

---

### Post by smrdelj on 2008-04-30
> **euzkoarima said:**
> Ni idea de que es el steam, pero busqué y encontré [esto]("http://ubuntuforums.org/archive/index.php/t-47169.html") que quizás te sirva. En particular fijate al final, que dice que es un problema de fonts (Tahoma).

Suerte.Gracias por responder. Todo bien master, pero ¿Qué tiene que ver eso con lo q pregunto? :S

La font Tahoma es fundamental para poder ver los textos, pero no para correr el juego. Ya me pasó en Ubuntu 7.10 y la instalé. Tambien la tengo en 8.04. Pero la verdad q no tiene nada q ver con lo q a mi me pasa :S

Gracias de todas formas

Alguna otra idea? Saludos

---

### Post by faktorqm on 2008-05-01
Me tuve que ir hasta los foros de Wine a ver que estaba pasando...

Este es el post que encontre que es identico a tu problema: [http://forum.winehq.org/viewtopic.php?t=242](http://forum.winehq.org/viewtopic.php?t=242)

Ahi proponian algunas cosas, resumiendo proba esto:

```
wget [http://kegel.com/wine/winetricks](http://kegel.com/wine/winetricks)
sh winetricks gecko
```

Si no llega a andar eso, probamos otras cosas. De paso leete la bibliografia que me lei yo para ayudarte a vos asi de paso somos 2 los que sabemos del problema en lugar de uno. Salu2!!!

Bibliografia consultada:
[http://wiki.winehq.org/FAQ](http://wiki.winehq.org/FAQ) (FAQ de wine)
[http://www.tatanka.com.br/ies4linux/page/Main_Page](http://www.tatanka.com.br/ies4linux/page/Main_Page) (Internet explorers para linux)
[http://bugs.winehq.org/show_bug.cgi?id=10090](http://bugs.winehq.org/show_bug.cgi?id=10090) (Pagina donde esta reportado el bug de wine)
[http://wiki.winehq.org/winetricks](http://wiki.winehq.org/winetricks) (Pagina del winetricks)

---

### Post by MeduZa on 2008-05-01
instala winedoors que y luego desde el instalas steam y todo lo demas!

suerte

---

### Post by smrdelj on 2008-05-01
Hola muchachos, que tal. El Gecko por fin pude instalarlo. Lo hice manualmente, siguiendo los pasos de este topic: [http://ubuntuforums.org/showthread.php?t=634464](http://ubuntuforums.org/showthread.php?t=634464)

Igualmente, si bien consigo que Steam logguee (para ello requería Gecko), ahora tengo el problema de que al indicarle que instale el Cs, se me cierra todo a la ******. Toy cada vez mas cerca jajaja :P

faktorqm, muchas gracias por tu esfuerzo. Ahora en un rato me pongo a leer todo y posteo o edito.

MeduZa, el Wine-Doors ya lo tengo instalado, pero me resulta de lo más inestable. Creo q tiene zarpadas incompatibilidades con Ubu Hardy 8.04
Nada de lo q instalé via Wine-Doors me ha corrido (incluso un par de cosas me dieron error). Es más, ni siquiera puedo desinstalarlo. Es un cancer! la **** madre! jaja

Saludos, muchas gracias

---

