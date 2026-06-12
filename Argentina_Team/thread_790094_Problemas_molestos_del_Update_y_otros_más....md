---
title: "Problemas molestos del Update y otros más..."
date: 2008-05-11
forum: Argentina Team
---

### Post by Kabezon on 2008-05-11
Buenas, una vez más :P Estuve lidiando con estos problemines por 1 semana, logré resolver algunas y otros siguen en pie. Les dejo un listadito, por ahí alguno se encontró con los mismos al actualizar a esta última versión o en algún otro momento. También aprovecho a nombrar unos que los sufro desde siempre.

A) Problema molesto con las sesiones:
- ¡Desde el update se descontroló todo! Hay aplicaciones que en el start up arrancan doble, otras que arrancan vaya uno a saber por qué, ya que yo no las programé, y otras que sí deberían abrirse no lo hacen.
- A veces al arrancar andá TODO mal... Me veo forzado a resetear la máquina, y desde el botón del CPU, porque Linux no me permite hacerlo :S!

B) Exaile:
- Hace Fetch sólo a los álbumes que se le da la gana.
- La transparencia del notificador no funciona

**[COLOR="Red"][Solved][/COLOR]**K3B (No sé si sea un problema o si el K3B es así)
- No me deja grabar MP3s a un CD de Audio O.O Me pide que sean archivos wave, y eso? Me falta instalar algo?

D) No puedo mover archivos arrastrándolos. La mayoría de las veces se congela todo y a los 10 segundos aproximadamente vuelve a andar, pero los archivos no se copiaron. Me veo forzado a hacer cut and paste para evitar este frecuente inconveniente.

E) Al navegar mucho por mis archivos (cosa que hago sólo al meterle música a mi PSP) Nautilus empieza a fallar... Me dice que el contenido de x folder no puede ser visto :S!!

F) A veces la hora del reloj se congela... El otro día mis amigos me querían matar, como el reloj se me había clavado en las seis y media, llegué 40 min tarde a la película, que por cierto estuvo muy buena, y eso que me perdí 30 min :P vayan a ver Iron Man! Y a Meteoro, ni se gasten, al menos que lleven a sus hijos chiquitos :P El problema del reloj pasa rara vez, pero me pareció algo importante...

G) Firefox se vive colgando! El problema aparenta ser el Flash :S Antes me pasaba, pero muy poco, ahora es demasiado seguido -.-

Desde ya les agradezco, porque sé que como siempre van a contestar con la mejor onda =]

---

### Post by Hei Ku on 2008-05-11
lo del K3B, es que para rippear mp3 te hace falta una biblioteca aparte. El k3b te avisa que necesitas una biblioteca aparte para eso.

Fijate si tenes instalado el paquete libk3b2-mp3.

---

### Post by WanderingKnight on 2008-05-11
>  A) Problema molesto con las sesiones:
 - ¡Desde el update se descontroló todo! Hay aplicaciones que en el start up arrancan doble, otras que arrancan vaya uno a saber por qué, ya que yo no las programé, y otras que sí deberían abrirse no lo hacen.
 - A veces al arrancar andá TODO mal... Me veo forzado a resetear la máquina, y desde el botón del CPU, porque Linux no me permite hacerlo :S!

Eso es grave... fijate en el menú "Sessions" de GNOME. La verdad no sé bien que decirte al respecto.

>  
 B) Exaile:
 - Hace Fetch sólo a los álbumes que se le da la gana.
 - La transparencia del notificador no funciona

No conozco Exaile, pero tené en cuenta que es soft nuevito y ese tipo de cosas suelen ocurrir.

>  
 C) K3B (No sé si sea un problema o si el K3B es así)
 - No me deja grabar MP3s a un CD de Audio O.O Me pide que sean archivos wave, y eso? Me falta instalar algo?

Como dijo Hei Ku, seguramente necesitás una biblioteca que actua como front-end de un conversor de mp3 a wav. Fijate de instalarla.

>  D) No puedo mover archivos arrastrándolos. La mayoría de las veces se congela todo y a los 10 segundos aproximadamente vuelve a andar, pero los archivos no se copiaron. Me veo forzado a hacer cut and paste para evitar este frecuente inconveniente.

 E) Al navegar mucho por mis archivos (cosa que hago sólo al meterle música a mi PSP) Nautilus empieza a fallar... Me dice que el contenido de x folder no puede ser visto :S!!

...

 
 G) Firefox se vive colgando! El problema aparenta ser el Flash :S Antes me pasaba, pero muy poco, ahora es demasiado seguido -.-

Eso es un problema bastante serio. Al parecer, tu procesador no se lleva bien con el nuevo scheduler que le agregaron al kernel desde el upstream... Además, hay que tener en cuenta que en Hardy se mandaron la ***** de [activar mal una opcion](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/188226). Chequeá que no tengas procesos "niced" (con prioridad) porque eso empeora las cosas debido a este bug.

La mejor manera de diagnosticar esto es corriendo top cuando veas que se te traba todo para ver qué proceso te esta comiendo todo el CPU.

Otra cosa, porque a mí me paso y estuvo todo muy inestable sin que yo supiera por que: Fijate si el sistema te esta montando la partición swap. Ubuntu usa un sistema de UUIDs para montar particiones con el fstab, y si formateaste la partición swap (ya sea porque instalaste otro sistema operativo o por lo que fuere) la UUID cambia y cuando el sistema va a buscarla no la encuentra. En el caso del swap, por alguna razon nunca me avisó que no la estaba montando (cuando pasa con otras particiones se corta el booteo para avisarte que algo está mal), y por eso me pasaban cosas raras tipo programas cerrándose porque sí y ese tipo de cosas. Ya se que es medio extraño, pero me ha pasado y la verdad me costaba saber por qué.

> F) A veces la hora del reloj se congela... El otro día mis amigos me querían matar, como el reloj se me había clavado en las seis y media, llegué 40 min tarde a la película, que por cierto estuvo muy buena, y eso que me perdí 30 min :P vayan a ver Iron Man! Y a Meteoro, ni se gasten, al menos que lleven a sus hijos chiquitos :P El problema del reloj pasa rara vez, pero me pareció algo importante...

Eso ya me parece que puede tirar para el lado de un problema de hard... el reloj es el interno de la máquina, tal vez le está llegando la hora final a la batería. De todas formas me parece algo extraño.

---

### Post by Hei Ku on 2008-05-11
Por el tema de la hora, recuerdo que en Breezy tenia un problema similar, aunque no tanto. Lo que me pasaba a mi era que para mi chipset, habia un problema con la gestion de power, asi que cada tick de procesador era como 2, el reloj terminaba ganando media hora por cada hora, y tuve que ponerle el ntp para hacer update de la hora cada un rato.
Fijate por problemas entre tu chipset y el kernel de hardy. Espero que no sea eso.

---

