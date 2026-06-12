---
title: "Por Favor Ayuda Para Efectos 3 D !!!!"
date: 2007-11-12
forum: Argentina Team
---

### Post by leonardo83 on 2007-11-12
Que tal gente, antes de decirles mi inquietud les agradezco la mano que me estan dando, la  verdad que sin el foro creo que ya habria renunciado a linux porque la mayoria de mis amigos no saben nada del tema y a pesar de toda la informacion de internet siempre esto me parecio un poco mas "personalizado" j aja.
Bueno, empecemos:
Por lo que puse en posts anteriores ya soy un feliz usuario de ubuntu 7.04 con un par de themes y un par de modificaciones hechas (siempre menores, fondos, iconos, etc).
Lo que quiero hacer es poner ese efecto 3d del escritorio, ademas del cubo en 3d.
En ubuntu fui a la opcion que dice efectos y me aparece EN GRIS las opciones de las ventanas y que el cubo gire, por lo que no puedo elegir nada, solo un boton abajo que me dice habilitar.Lo normal es que haga algo y me pregunte si deseo guardar los cambios verdad? bien, cuando elijo eso mi pantalla se pone BLANCA por aprox 1 minuto, y regresa y no hizo nada, sigue esa ventana.
No tengo idea como hacer para instalar eso del escritorio, lei bastante pero no se como instalar beryl (creo que se llama asi), ademas de que no se si se puede hacer de otra forma que no sea online porque puedo bajar el archivo que sea en la facu y luego instalarlo en casa (si, no tengo adsl :( )
Muchas gracias amigos, espero respuesta! :(:(:(:(:(:(

PD: me colgue, tengo una placa con acel. grafica sniper2 Riva tnt2 M64, viejita pero anda!!

---

### Post by clasificado on 2007-11-13
¿y le instalaste los controladores restringidos?

ubuntu viene por defecto con los modulos open source, que es mejor evitar para la aceleración 3d si sos nuevo en esto.

Reemplazandolos por los controladores restringidos tenes mas chance de tener el cubo feo ese.

Clasificado

---

### Post by leonardo83 on 2007-11-13
> **clasificado said:**
> ¿y le instalaste los controladores restringidos?

ubuntu viene por defecto con los modulos open source, que es mejor evitar para la aceleración 3d si sos nuevo en esto.

Reemplazandolos por los controladores restringidos tenes mas chance de tener el cubo feo ese.

Clasificado

Ok pero para man, me hablas como si supiera sobre lo que me estas diciendo vamos despacio :confused:
no se de que controladores restringidos me hablas ni como fijarme eso, por lo que te decia soy muy novato en esto :(

................... S.O.S ..............:confused:

---

### Post by tzulberti on 2007-11-13
Lo que esta comentandote clasificado es si instalastes el driver para tu placa de video. Es decir, Ubuntu te lo detecta pero te pone algo similar a un driver generico el cual no tiene aceleracion 3d. Para instalar el driver de tu placa tenes que ir a System -> Admin -> Restricted Modules (o algo asi). Tildar la opcion de tu placa de video.

Luego reiniciar, y volver a intentar poner los efectos 3d.

---

### Post by leonardo83 on 2007-11-13
Gracias muchachos.
Me fije esa parte que me dicen pero me aparece cargada mi placa, ahi esta la riva tnt2, no tuve que cambiar nada.
Sera problema de mi hard o tendre que modificar algo por consola ?
:( :( :(

Saludos....

---

### Post by Exegete on 2007-11-13
Leonardo83, que tipo de tarjeta de video tiene?  Antes de instalar una tarjeta de video (ATI Radeon, con algunas problemas en la instalación) mi escritorio no podia hacer los efectos 3D.  Pero despues de añadir la tarjeta de video, ahora lo hace perfectamente - y tengo muchos mas efectos en el menu para elegir.  Creo que sin la tarjeta de video no tenía bastante memoria ni poder para usar los efectos 3D.

---

### Post by sajnox on 2007-11-13
Skavenger hoy posteo una guia para habilitar efectos en Ubuntu que parece muy facil y practica.

[http://ubuntuforums.org/showthread.php?t=611923](http://ubuntuforums.org/showthread.php?t=611923)

Si haciendo eso no funciona, en una terminal escribi

```
 $ compiz --help
```

Y nos posteas lo que te devuelve

---

### Post by leonardo83 on 2007-11-13
> **Exegete said:**
> Leonardo83, que tipo de tarjeta de video tiene?  Antes de instalar una tarjeta de video (ATI Radeon, con algunas problemas en la instalación) mi escritorio no podia hacer los efectos 3D.  Pero despues de añadir la tarjeta de video, ahora lo hace perfectamente - y tengo muchos mas efectos en el menu para elegir.  Creo que sin la tarjeta de video no tenía bastante memoria ni poder para usar los efectos 3D.


Una riva tnt2 m64, lo puse al principio, y esta (creo) instalada, igual no es ATI.
Gracias man.

---

### Post by Exegete on 2007-11-13
Leonardo83, leí el posteo de Sajnox, y la guia (de Skavenger) que él describe es exactamente lo que se necesita.

---

### Post by leonardo83 on 2007-11-13
> **sajnox said:**
> Skavenger hoy posteo una guia para habilitar efectos en Ubuntu que parece muy facil y practica.

[http://ubuntuforums.org/showthread.php?t=611923](http://ubuntuforums.org/showthread.php?t=611923)

Si haciendo eso no funciona, en una terminal escribi

```
 $ compiz --help
```

Y nos posteas lo que te devuelve


Gracias sajnox, mira vi ese post pero es para ubuntu 7.10, creo que hay opciones que mi version no tiene.
Voy a escribir eso en consola y lo posteo aca, gracias! :)

---

### Post by rretamar on 2007-11-13
Está bueno ese avatar de Kerry King.

:)

(disculpen el "fuera de tema")

Linux + Metal = GLORIA TOTAL

Saludetes !

---

### Post by leonardo83 on 2007-11-13
> **rretamar said:**
> Está bueno ese avatar de Kerry King.

:)

(disculpen el "fuera de tema")

Linux + Metal = GLORIA TOTAL

Saludetes !

Esto ya es demasiado. Ademas de encontrar gente que te ayuda ademas comparten algunos la pasion por la misma musica que uno, que barbaro!
Saludos man, no desvirtuemos el thread, cualquier cosa si queres hablamos por msn y nos pasamos musica o charlamos un rato.
Ahora si, que siga el thread!!!

---

### Post by sajnox on 2007-11-13
Terminado el OT sigue el thread, muy bien!!!!

Segui [ESTA]("http://tuxpepino.wordpress.com/2007/06/30/instalar-compiz-fusion-en-ubuntu-feisty/") guia, los consejos de este pibe nunca fallan

Despues no contas si este funciona

---

### Post by leonardo83 on 2007-11-14
> **sajnox said:**
> Terminado el OT sigue el thread, muy bien!!!!

Segui [ESTA]("http://tuxpepino.wordpress.com/2007/06/30/instalar-compiz-fusion-en-ubuntu-feisty/") guia, los consejos de este pibe nunca fallan

Despues no contas si este funciona


gracias !!!

voy a probarlo y despues les digo como me fue... 

saludos :)

---

### Post by leonardo83 on 2007-11-14
> **tzulberti said:**
> Lo que esta comentandote clasificado es si instalastes el driver para tu placa de video. Es decir, Ubuntu te lo detecta pero te pone algo similar a un driver generico el cual no tiene aceleracion 3d. Para instalar el driver de tu placa tenes que ir a System -> Admin -> Restricted Modules (o algo asi). Tildar la opcion de tu placa de video.

Luego reiniciar, y volver a intentar poner los efectos 3d.


ACTUALIZACION :
-------------------

me puse a hacer esto, entre en restricted modules y encontre mi placa.
Aparece mi placa y tiene un cuadradito que se puede marcar y aln lado un circulo rojo que dice "no esta en uso"  o algo similar.
Hago click en el cuadradito para habilitarlo y me aparece una ventana que dice "habilitar controlador?" , eligo aceptar ´... piensa unos momentos y vuelve a aparecerme esa ventana y sigue diciendo que no lo tengo habilitado y que no esta en uso.
Que tengo que hacer?
Tengo que usar el cd con los drivers o algo???  :confused::confused::confused:

Saludos!!

---

