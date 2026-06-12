---
title: "nvidia y ubuntu 7.10 ¿compatibles?"
date: 2007-11-28
forum: Argentina Team
---

### Post by leonardo83 on 2007-11-28
que tal gente , tengo una consulta.
Tengo una placa nvidia riva tnt2, algo viejita y ubuntu 7.10.
Fui a controladores restringidos y no me deja habilitar la placa, la pantalla aparece en blanco y no sucede nada. :confused:
En esta parte, aparece nvidia[COLOR="Magenta"] (para placas antiguas)[/COLOR]... es decir , vi que los demas cuando hacen esto les aparece como "placas modernas" o "placas actuales". que no es mi caso.
Mi pregunta es entionces, es compatible mi placa para ubuntu?
Ya habia especificado mi pc en posts anteriores pero bue, pentium 3 750 mghz, rigido de 80 gb y 640 de ram.
Avisenme si se puede habilitar bajando algun archivo quizas de internet o si solo puedo utilizar los efectos de escritorio adquiriendo una nueva placa, y en ese caso cual :( :( :(.

Saludos!!

---

### Post by guillermolisi on 2007-11-29
Leonardo

Ese tipo de placas funciona pero con los legacy drivers. Tengo una Compaq Deskpro con Celeron de los viejos, epoca de P II, y 256 Mb funcionando con Feisty y esa misma placa (64 Mb) desde hace meses con los drivers antiguos. En cuanto pueda la actualizo a Gutsy.

Ojo que no tiene aceleracion grafica como para hacer funcionar Compiz y equivalentes.

Si queres usar Compiz o cualquier otro efecto que precise de aceleracion grafica, mi consejo (por ahora) es "comprate una placa con chip nVidia. Si es posible, con memoria on board, que no tome RAM de la motherboard".

---

### Post by vk-cdg on 2007-11-29
> **leonardo83 said:**
> ... o si solo puedo utilizar los efectos de escritorio adquiriendo una nueva placa, y en ese caso cual :( :( :(.

Saludos!!

En mi caso tengo una nVidia Geforce 7300 GT con 256 de ram y anda de 10, ni un solo problema. 
El único inconveniente que tuve con Gusty fue que no supo detectar el modelo de mi monitor por lo que no me respetaba la frecuencia de barrido. Nada que no se pueda solucionar reconfigurando el xorg.conf

---

### Post by guillermolisi on 2007-11-29
Si, tembien tuve alguna historia con una instalacion de cero en una maquina que ya estaba usando Fesity con una nVidia 6200 sin problemas.

Cuando el hardware paso a ser usado por Gutsy tuve que laburar y "sudar" un poquito con los drivers nvidia hasta que volvio a su normal funcionamiento.

Nada que no se pueda resolver y hay buena documentacion al respecto en los foros, bLogs y sites. Estabilizado el tema de la placa acomode el modelo del monitor.

---

### Post by User21 on 2007-11-29
En mi humilde opinion, con esa placa YO NI PENSARIA en usar COMPIZ. Personalmente, utilizaria esos recursos en simplemente hacer funcionar mi pc, dandole vida con xfce o enlightenment, y NADA de eyecandy. Saludos!

---

### Post by clasificado on 2007-11-29
El nombre del paquete que corresponde a los drivers antiguos de nvidia es el 

**nvidia-glx-legacy**

probá instalando esos

---

### Post by HorD on 2007-11-29
nosé si será tu caso pero a mi me sirvió en su momento... por las dudas lo dejo.. [http://kmandla.wordpress.com/2007/03/25/success-compiling-nvidia-8776-driver-on-feisty-2620-12-386/]("http://kmandla.wordpress.com/2007/03/25/success-compiling-nvidia-8776-driver-on-feisty-2620-12-386/")

saludos!..

---

### Post by leonardo83 on 2007-11-29
> **User21 said:**
> En mi humilde opinion, con esa placa YO NI PENSARIA en usar COMPIZ. Personalmente, utilizaria esos recursos en simplemente hacer funcionar mi pc, dandole vida con xfce o enlightenment, y NADA de eyecandy. Saludos!

:confused: lo que ???? :confused:




A los demas, gracias manes, mi consulta es si con mi placa viejita se va a poder ver el cubo ese y toda la bola, no se si se podra, me fije la caja de la placa y dice que tiene aceleracion 3d y bla bla bla, asi que no deberia tener problemas.............o si?

Instalando ese archivo legacy que me dicen se solucionaria? :(
Gracias!

---

