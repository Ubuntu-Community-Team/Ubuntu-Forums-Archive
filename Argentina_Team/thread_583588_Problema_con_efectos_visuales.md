---
title: "Problema con efectos visuales"
date: 2007-10-20
forum: Argentina Team
---

### Post by Applelnx on 2007-10-20
Hola, soy bastante nuevo con linux. Estuve en Cafeconf (yo fui el que estuve molestando a Felipe Lerena para que me diera stickers de Mozilla y Ubuntu jaja) y ayer instale el Ubuntu 7.10. Tengo un problema con los efectos visuales me tira el siguiente error:

[IMG]http://img98.imageshack.us/img98/893/pantallazoxy7.png[/IMG]

Alguien sabe que puede ser? Tengo una placa integrada (512 de ram de los cuales 64 van para video)

Saludos

---

### Post by lordpuppet on 2007-10-20
Para tener los efectos visuales disponibles hay que tener instalados los drivers de video. 

Si tenes una placa nvidia hay que instalar el paquete nvidia-glx-new del sinaptic. A mi me lo instalo cuando quise poner los efectos automaticamente, me sorprende que no te de esa opción.

Que placa de video tenes?

---

### Post by Applelnx on 2007-10-20
ATI
Radeon Xpress 200

---

### Post by juanman on 2007-10-20
El soporte de ati todavia no es muy bueno, pero acaban de liberar sus drivers, asi q es cuestion de tiempo a q salga algo decente...
[Aca tenes un manual]("http://damr.net/blog/2007/10/19/howto-compiz-fusion-en-ubuntu-gutsy-710-ati-radeon-xpress-200m/")...

---

### Post by steve_ignorant on 2007-10-20
bueno pido ayuda aca, ya que esta con el mismo problema de que no puede cargar. 

a mi me ocirrio esto: 

intalo ubuntu, preparo todo conecto a internet todo muy lindo... 

hasta ahi todo bien, bajo paquetes de Nvidia, intento configurar el compiz, hasta que: 

me empezo a funcionar medio raro, como que se me colgaban las ventanas que pasaban a estar en un segundo plano y todo ese tipo de cosas. decidi reiniciar para ver que pasaba. reinicio y me encuentro conque ubuntu entra en " amodo de prueba de fallos" y no me reconoce la placa de video... 

bueno, consigo los drivers apropiados, y toda la historia que ya se conoce y ahi... pongo "sh nvidia-linux-x86-96.43.01-pkg1.run" tal cual dice la pagina(con el X apagado lo hice) y me dice " no se puede abrir el archivo o error al ejecutar el archivo, (y si al driver si lo ejecuto en el entorno grafico me dice que lo tengo que correr del root entrnado al asistente...) 


 si me pueden decir como puedo hacer, baje un tutorial para hacerlo pero... me sucedio lo mismo.... 
gracias, igualmente intentare hacer a ese tutorial de nuevo. pero espero alternativas. gracias.

---

### Post by WanderingKnight on 2007-10-20
Applelnx: hace algo, abri una consola y tipea compiz. Si no arranca, postea aca el error que te tira.

De todas formas, lo mas probable es que te falten los drivers de ATI o tengas que ponerlo en modo xgl.

---

### Post by Applelnx on 2007-10-21
Este es el error que me tira:

[IMG]http://img85.imageshack.us/img85/6489/compizpo7.png[/IMG]

como lo pongo en modo xgl?

---

### Post by Hernán-Amaya on 2007-10-21
en este thread se trato el tema [http://ubuntuforums.org/showthread.php?t=574250](http://ubuntuforums.org/showthread.php?t=574250)

---

