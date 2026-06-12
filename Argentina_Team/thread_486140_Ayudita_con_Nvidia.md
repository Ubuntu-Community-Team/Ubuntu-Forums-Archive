---
title: "Ayudita con Nvidia"
date: 2007-06-27
forum: Argentina Team
---

### Post by Mauro22 on 2007-06-27
Como les va??

Les comento, hoy (no se porque) se me ocurrio bajar el Envy, para que me baje los ultimos drivers disponibles de mi Nvidia Geforce 6200. Todo iba bien, lo bajo, lo instalo, y me pidio reiniciar y asi fue.

Aqui el problema, el modo grafico no levanta mas. Dice erro de startx y que el driver no corresponde a la placa etc etc etc.

Alguien sabe como se puede volver atras??


PD: Si las cosas andas, no las toquen. ;)

Saludos y gracias de antemano!

---

### Post by clasificado on 2007-06-27
> Si las cosas andas, no las toquen.
Yo no termino de asimilar esta :D disfruto reventando mi máquina.

y no. Todavia el tiempo atras no vuelve ;) (que yo sepa) 

Lo que podemos hacer es arreglar la macana que se mandó el Envy, te puedo dar tres consejos:

1) Cambiate en el /etc/X11/xorg.conf, la linea del  [Driver "nvidia"] por  [Driver "nv"] asi volves a tener entorno gráfico (aunque no va a levantar el beryl)
¡y necesitamos mas info! por lo que:

2) Posteate tu /etc/X11/xorg.conf, asi vemos que hizo envy, y:

3) Posteate el log de xorg. está en /var/log/Xorg.0.log (usualmente)
Con ésto ultimo hay un detalle, cada vez que inicia, reemplaza el log que ya existe (...cosa que no me gusta nada...). Por lo que si encendés el motor grafico con el driver NV, vas a borrar el log del error con el driver Nvidia :P

nada más.

Clasificado

---

### Post by Mauro22 on 2007-06-27
```
Gracias x la respuesta.

Les comento lo que hice:

ejecute:
[CODE]sudo dpkg-reconfigure xserver-xorg
```

Con esto pude levantar el modo grafico, usando los drivers "vesa", ya que ni nv ni nvidia resulto.

Una vez en modo grafico, elimine el driver bajado con el envy y cambie el xorg.conf por el xorg.conf.backup (que genera el envy (menos mal jeje))

Ahora es asi, usando ubuntu con drivers vesa generico, sin ningun efecto ni nada.

Salu2!![/CODE]

Al final tuve que volver a instalar el ubuntu, activar el controlador restrigido y listo.

Resumiendo, placa de video Nvidia GeForce 6200 (256mb) NO hay que actualizar los drivers.

Salu2!

---

