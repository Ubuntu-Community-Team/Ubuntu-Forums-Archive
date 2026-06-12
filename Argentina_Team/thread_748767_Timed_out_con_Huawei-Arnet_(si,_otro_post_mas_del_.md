---
title: "Timed out con Huawei-Arnet (si, otro post mas del alfajor...)"
date: 2008-04-07
forum: Argentina Team
---

### Post by kha0s101 on 2008-04-07
[COLOR="DarkGreen"]Hola.

Cumpliendo con el propósito de "despertar" a algunos que aún están conectados a güindou$, convencí a un amigo de instalar en su compu el Ubuntu 7.10 y anda todo espectacular (reconoció todo el hard sin protestar), hasta llevé paquetes que había bajado para mí y todo funcionó sin mayores problemas. Peeeero, al intentar conectar a Arnet resultó imposible o mejor dicho, no sé que resultó...

Seguí las guías que encontré en el foro (y que me funcionaron en MI pc). De hecho, no existieron errores ya que el maldito alfajor conecta bien (leds power y link encendidos y sin parpadear) pero no hay caso, hecho todo el trabajo, al ejecutar: 

**pppoe-start** 

envía datos y al final solo dice[/COLOR] [COLOR="Red"]**TIMED OUT**[/COLOR]

[COLOR="DarkGreen"]Si ejecuto

**pppd call adsl**

me dice que: **Plugin rp-pppoe.so loaded**... pero no se puede navegar :confused:

En suma, todo parece estar bien, ya que indica que el modem está operacional,  el servicio pppoe funciona bien, pero no se puede acceder a internet desde ninguna aplicación.
Busqué en los foros sin éxito para este problema... Alguien sabe como solucionarlo? 

Saludos.[/COLOR]

Se trata de un MT810 de diabólicas luces rojas!! aunque ví que los Huwaei (810 luces rojas o verdes o el 882) tienen un procedimiento de instalación.

---

### Post by Hei Ku on 2008-04-07
que te dice si pones ifconfig?

---

### Post by kha0s101 on 2008-04-08
[COLOR="DarkGreen"]Hola. Gracias por responder. 

La imagen muestra el resultado de ifconfig.

[img]http://www.pic2up.net/RDVDRzO.png[/img]

lo cual es poco menos que latín para mi, je.

Saludos.



[/COLOR]

---

### Post by UBUjuan on 2008-04-09
debe ser que no pusiste sudo br2684ctl -c 0 -b -a 0.33 antes de ifconfig nas0 up

---

### Post by kha0s101 on 2008-04-09
[COLOR="DarkGreen"]Probé rehaciendo el tuto completo pero no, sigue pasando lo mismo del Timed Out :([/COLOR]

---

### Post by mauriciog on 2008-04-09
kha0s101 (nick complicadito eh?)
Si te fijas en la información del adaptador nas, no tenés asignada una IP al dispositivo por parte de Arnet.
Trabajé para esa compañía dando soporte algunos años y la experiencia me dice que, lo mejor que puedo recomendarte, es que cambies ese modem por uno ethernet.
Pedí el cambio por incompatibilidad de tecnología a la opcion 3 (Customer Care) del 0800 pero no menciones que utilizas Linux porque no dan soporte para este sistema operativo.
Saludos!

---

### Post by kha0s101 on 2008-04-11
[COLOR="DarkGreen"]Hola.

Gracias por la idea Mauricio, la comento a mi amigo. Que se juegue a ver si consigue un modem ethernet a buen precio de Arnet. Aunque, si no me equivoco hace como 2 o 3 años ya que tiene ese modem. Lo raro es que el cd de instalación del Huawei sí que trae unos paquetes para Linux, pero son rpm si no me equivoco y viejos, claro. Sin embargo, parecería indicar que dan la opción de usar el modem (y el mismo suporte se supone), bajo Linux. Pero estoy seguro que no es así, porque las respuestas que dan son de manual y son para M$... 

Gracias por la respuesta. Aviso como le fue.

P.S.: nick compicado, jeje lo sé!!! es mi pasado matrixero que no me abandona, *the problem is the choice 8-)*[/COLOR]

---

### Post by abautist on 2008-04-11
yo puse arnet ayer y me mandaron el huawei smartax mt882.

No existe nada como el zyxel prestige 600 q te da speedy, pero bue, por lo menos podes conectarte bien.

Salutes

---

