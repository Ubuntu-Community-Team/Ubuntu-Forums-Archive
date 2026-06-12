---
title: "Cambio de placa de video"
date: 2007-09-07
forum: Argentina Team
---

### Post by rojojuan on 2007-09-07
Dentro de unos días voy a instalar una placa de video (seguramente de NVidia para evitar problemas). Actualmente tengo una on board. Cuando lo haga, tendré problemas con el Ubuntu 7.04 que estoy corriendo? Algo para tener encuenta?

---

### Post by SLA_leandrin on 2007-09-07
No vas a tener problemas con una placa nvida... creo que son las placas de video que mejor funcionan, seguramente los muchachos con más conocimientos podrán decirtelo mejor...:) yo tengo una nvidia y anda sin ningún problema, perfecto, en cambio con la placa de sonido de creative estoy luchando, no te recomiendo esa compra, ni nada de marca creative!!

Nada mas tenés que instalarle los drivers:
```
sudo apt-get install nvidia-glx
```

Si le vas a conectar la tele te recomiendo que le instales el nvidia-tvout, funciona muy bien.

Sino también lo podes instalar usando automatix...

Saludos!

---

### Post by Mataca on 2007-09-07
Rojojuan

Yo tengo una nvidia fx5700 le 256mb y la verdad no tuve ni tengo ningun drama. A mi parecer son muy compatibles con Ubuntu. También evangelice otra pc con otra nvidia y 0 problems.

Por otro lado Ati esta sacando nuevos drivers para open source (antes apestaban) pero como no los probé, no te voy a recomendar que compres una Ati.

Hasta lo que yo se, no vas a tener dramas

---

### Post by rojojuan on 2007-09-07
> **SLA_leandrin said:**
> No vas a tener problemas con una placa nvida... creo que son las placas de video que mejor funcionan, seguramente los muchachos con más conocimientos podrán decirtelo mejor...:) yo tengo una nvidia y anda sin ningún problema, perfecto, en cambio con la placa de sonido de creative estoy luchando, no te recomiendo esa compra, ni nada de marca creative!!

Nada mas tenés que instalarle los drivers:
```
sudo apt-get install nvidia-glx
```

Si le vas a conectar la tele te recomiendo que le instales el nvidia-tvout, funciona muy bien.

Sino también lo podes instalar usando automatix...

Saludos!

La única duda que tengo es si cuando arranca Ubuntu y detecta el cambio de hardware te da algún problema para instalar la placa nueva. Ah! y gracias por responder.
En otra máquina instalé el TvOut y funciona de maravillas!

---

### Post by faktorqm on 2007-09-07
mira, yo nunca lo hice, pero seguro seguro, lo que va a pasar es lo siguiente:
vas a arrancar el ubuntu, todo normal, pero el x no va a arrancar por que va a decir que no encuentra el hardware, entonces vas a una consola, le pones el driver nv, y reinicias. (con escribir sudo reboot alcanza)
entonces ahi te va a iniciar sin aceleracion grafica, pero vas a ver todo, ahi instalas el driver que quieras, si el original, desde envy o desde el gestor de controladores restringidos.
igual la idea de todo es que deshabilites la placa on board desde el bios, por que sino ubuntu te va a iniciar con la onboard y a la otra capaz no le da bolilla. contame como te fue. salu2!

---

### Post by rojojuan on 2007-09-08
> **faktorqm said:**
> mira, yo nunca lo hice, pero seguro seguro, lo que va a pasar es lo siguiente:
vas a arrancar el ubuntu, todo normal, pero el x no va a arrancar por que va a decir que no encuentra el hardware, entonces vas a una consola, le pones el driver nv, y reinicias. (con escribir sudo reboot alcanza)
entonces ahi te va a iniciar sin aceleracion grafica, pero vas a ver todo, ahi instalas el driver que quieras, si el original, desde envy o desde el gestor de controladores restringidos.
igual la idea de todo es que deshabilites la placa on board desde el bios, por que sino ubuntu te va a iniciar con la onboard y a la otra capaz no le da bolilla. contame como te fue. salu2!

Justo era el dato que necesitaba. Esta semana la instalo y te diré cómo me fue. Gracias por la respuesta, me resulta muy útil.

---

### Post by angelqpro on 2007-09-09
Ayer por fin AMD - ATI liberaron los drivers para las placas con GPU ATI. Parece ser que hay un notable incremento de rendimiento.
Estarán en la red el día 10 de este mes

[http://www.linux.com/feature/119049](http://www.linux.com/feature/119049)

---

### Post by Hei Ku on 2007-09-09
De todas maneras, a esta version del driver le faltan cosas. Recien para fin de año van a largar un driver con soporte de AIGLX y demas chiches. ATI todavia esta muy retrasado en cuanto a soporte de linux. Igual, dicen que esta version tiene muchas mejoras de performance, asi que aquellos que usan el driver propietario es recomendable que le den una probadita.

---

### Post by rojojuan on 2007-09-12
> **faktorqm said:**
> mira, yo nunca lo hice, pero seguro seguro, lo que va a pasar es lo siguiente:
vas a arrancar el ubuntu, todo normal, pero el x no va a arrancar por que va a decir que no encuentra el hardware, entonces vas a una consola, le pones el driver nv, y reinicias. (con escribir sudo reboot alcanza)
entonces ahi te va a iniciar sin aceleracion grafica, pero vas a ver todo, ahi instalas el driver que quieras, si el original, desde envy o desde el gestor de controladores restringidos.
igual la idea de todo es que deshabilites la placa on board desde el bios, por que sino ubuntu te va a iniciar con la onboard y a la otra capaz no le da bolilla. contame como te fue. salu2!

Les comento la experiencia que tuve con el cambio de la placa de video.
Pude hacerlo.
Probé cambiar en el xorg el driver a nv, pero no hubo caso.
Tuve que ir a dpkg -reconfigure.
Lo de la placa quedó bien, pero algunas secciones quedaron diferentes a como estaban antes; por suerte tenía impreso el xorg.conf inicial, así que hice las modificaciones para que todo quedara igual. Todo perfecto hasta aquí.
Aparecen las novedades.
Al setear la placa de video, veo que no aparece la clonación en las opciones. Traté varias formas para habilitarla pero no hubo caso; así que a googlear.
Ví que el problema es que hay que colocar un adaptador DVI – VGA y allí conectar la entrada del monitor y luego aparecerá la opción de clonación (para darle salida al TV).
Así que hoy compraré el adaptador y mañana les cuento que pasó.
Ah! ví que algunas placas traen ya ese adaptador, así que parece que esta el solución correcta.
Me apuré a hacer este comentario por si  alguien lo necesita.

---

### Post by clasificado on 2007-09-14
Gracias por el aporte

Mi adaptador vino con la placa

Clasificado

---

### Post by rojojuan on 2007-09-15
Bueno, al fin conseguí el adaptador, lo coloqué y arrancaron las opciones. Todo bien, así que solo era cuestión de colocar el adaptador.

---

