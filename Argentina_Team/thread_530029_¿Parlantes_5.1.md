---
title: "¿Parlantes 5.1?"
date: 2007-08-20
forum: Argentina Team
---

### Post by valucha on 2007-08-20
[COLOR="DarkOrchid"]Escribo nuevamente para preguntar como se hace una cosa :$
Recientemente me compré unos nuevos parlantes, que son de la siguiente marca y modelo: "Edifier M1500"
Yo cuento con una mother M2N-E de asus, que tiene la placa de sonido integrada "SoundMAX ADI AD1988"

La duda es la siguiente:
¿Cómo hago para hacer funcionar a los parlantes como unos parlantes 5.1? ... porque hasta ahora me funcionan como 2.1

Saludos y muchas gracias por responder

Valucha[/COLOR]

---

### Post by Mauro22 on 2007-08-20
Los parlantes 5.1 te van  a andar todos con un dvd o un juego que emita en 5.1


De lo contrario vas a tener siempre 2.1, o sea stereo


Salu2

---

### Post by valucha on 2007-08-20
[COLOR="DarkOrchid"]Pero supuestamente tienen que andar los demás parlantes... por ejemplo el del centro. En windows me andan todos los parlantes siempre.[/COLOR]

---

### Post by Mauro22 on 2007-08-20
Aunque no sea para tu placa por ahi sirve o te da una idea

[http://dudas.wordpress.com/2007/03/24/ubuntu-facil-sonido-51-en-ubuntu/](http://dudas.wordpress.com/2007/03/24/ubuntu-facil-sonido-51-en-ubuntu/)

Salu2

---

### Post by Hei Ku on 2007-08-20
cuando no estes pasando musica o sonido que sea 5.1 tenes que ponerle que te pase el sonido por el resto de los parlantes. En el alsa-mixer, o el controlador de volumen que tengas, tenes que ponerle "Duplicate front". Eso hace que por los parlantes de atras y del centro te duplique el sonido que sale por los frontales.

---

### Post by valucha on 2007-08-20
[COLOR="DarkOrchid"]Por ahora ninguna solución :([/COLOR]

---

### Post by por100pre1 on 2007-08-20
Si tienes un icono de volumen en uno de los paneles, pinchalo con el boton derecho del raton y presiona Abrir el control de volumen y verifica el volumen ahi. Si no funciona escribe esto en terminal:

```
lspci
```

y postea aqui el resultado a ver si tu tarjeta de audio es detectada correctamente... :-k

---

### Post by valucha on 2007-08-20
[COLOR="DarkOrchid"]Ya logré que funcionen todos los parlantes...
Ahora lo que pasa es que cada vez que reinicio se bajan todos los volumenes hasta quedar silenciados.
Como hago para que no se me bajen todos? :S[/COLOR]

---

### Post by MeduZa on 2007-08-20
ese tema ya esta recontravisto aca, a mi me paso lo mismo con la placa de sonido onboard, esas placas son malisimas y hacen todo por SOFTWARE, entonces los drives de ALSA asumen que si es 2.1 debe salir como tal, lo que podes hacer son 3 cosas:
1: cuando escuchas musica a tu reproductor le decis que use 5.1 (no se si todos lo tienen)
2: activas la copia de los frontal en lo lateral, aun asi ami no me andavan los del medio (ni el delantero y en mi caso el trasero (6.1) pero si te van a andar los 2 de atras de los lados)
3: editando un archivo (no me acuerdo cual) le podes poner que todo lo 2.1 se haga 5.1, yo lo probe pero no me gusto como andaba, o sea los parlantes sonaban incorrectamente (ej el derecho de atras hacia lo de el del medio y cosas asi)

Recomendacion (o lo que yo hice) me compre una audigy 2 que hace todo por hardware (mixeado y manejo de canales) y me anda de 10 y todo me sale por todos lados y como debe ser
Fijate que algunos sortware te permiten setear que la salida sea por 5.1

---

### Post by valucha on 2007-08-20
[COLOR="DarkOrchid"]Los parlantes andan... ahora el tema es que cada vez que reinicio la configuración vuelve a como si no la hubiera cambiado

Alguna solución para eso?[/COLOR]

---

### Post by Hei Ku on 2007-08-20
si estas usando el alsa-mixer, podes probar con el siguiente comando una vez que terminaste de configurarlo:
```

sudo alsactl store 0
```

---

### Post by valucha on 2007-08-20
[COLOR="DarkOrchid"]Solucionado...
Fue problema mio :P habia puesto un script que no iba.[/COLOR]

---

