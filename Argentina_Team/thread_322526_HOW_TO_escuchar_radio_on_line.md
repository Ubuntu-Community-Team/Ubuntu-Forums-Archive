---
title: "HOW TO escuchar radio on line"
date: 2006-12-20
forum: Argentina Team
---

### Post by elgatogordo on 2006-12-20
No se si les pasó, al intentar escuchar algunas radios argentinas online me encuentro con que al hacer click en el botón correspondiente de la respectiva página web se abre una ventanita y despues nada.
revisando el código fuente  me encuentro con un javascript que abre el windows media player (algunos se juegan e incluyen el real player) y empieza a reproducir el sonido.
¿la solución? buscar en el código fuente el origen la transmisión y pegarlo en nuestro reproductor de sonido preferido.
EJEMPLO
1) Vamos a [www.amdelplata.com](www.amdelplata.com)
2) Hacemos click en el botón EN EL AIRE
3) Llevamos el puntero al cuadrado vacio de la ventanita y haciendo click en el botón derecho seleccionamos VER CÓDIGO FUENTE DE LA PÁGINA
4) Buscamos en el código el origen de la transmisión (generalmente empieza en mms o termina en asx)
en nuestro caso
 src="DelPlata.asx"
        width=159
        height=125 type="application/x-mplayer2"
        pluginspage="http://www.microsoft.com/Windows/Downloads/Contents/Products/MediaPlayer/"
        filename="[COLOR="Red"]mms://delplata.telecomdatacenter.com.ar/delplata[/COLOR]"
        showcontrols=1
        showdisplay=1
        showstatusbar=1 autosize="0"> </embed>
5) Pegamos la dirección en nuestro reproductor preferido 
eb el caso de Totem ABRIR DIRECCIÓN

NOTA:
Teniendo en cuenta que en ningún foro encontre comentario alguno sobre el tema, debe haber alguna forma mucho más cómoda y fácil de hacer esto

---

### Post by daniminas on 2006-12-20
nunca pude esuchar radio en Ubuntu.... :-k .. porque será que estas cosas multimedia siempre parecen mas faciles en Windows.](*,)

---

### Post by elgatogordo on 2006-12-20
porque los diseñadores para no molestarse utilizan modulos desarrollados ¿a que no sabés por quien?

---

### Post by pump on 2006-12-20
Claro, es como las paginas que se ven mal con firefox. No es porque el firefox esta mal hecho sino que las paginas estan hechas para ie y no respetan el standard.

---

### Post by MeduZa on 2006-12-20
usa el media player conectivity (plugin del FF seamonkey /mozilla o netscape) y te va a andar cualquer cosa multimedia

[http://membres.lycos.fr/sethnakht/FAQ%20MediaPlayerConnectivity.html]("http://membres.lycos.fr/sethnakht/FAQ%20MediaPlayerConnectivity.html")
este link lo saque del about del plugin espero les sirva (lo saque del foro de ubuntu en ingles)

PD no es un plugin sino una extencion del browser

saludos

---

### Post by elgatogordo on 2006-12-21
Es la historia de mi vida,, dos meses buscando una solución y existia una mucho más fácil ¿ahora donde me meto la segunda parte del howto para escuchar radio y el de ver televisión por internet?. por favor no contesten. el link para bajarse la extensión es
[http://releases.mozilla.org/pub/mozilla.org/extensions/mediaplayerconnectivity/mediaplayerconnectivity-0.8.3-fx+fl+mz+ns+zm.xpi](http://releases.mozilla.org/pub/mozilla.org/extensions/mediaplayerconnectivity/mediaplayerconnectivity-0.8.3-fx+fl+mz+ns+zm.xpi)

---

### Post by elgatogordo on 2006-12-21
Me quede pensando en eso de que hago de la manera más dificil lo que se puede hacer fácil. ¿no tendria que pedir trabajo en microsoft?
Gracias MeDuZa. muy bueno tu aporte

---

### Post by jpmorelli on 2006-12-21
> **MeduZa said:**
> usa el media player conectivity (plugin del FF seamonkey /mozilla o netscape) y te va a andar cualquer cosa multimedia

[http://membres.lycos.fr/sethnakht/FAQ%20MediaPlayerConnectivity.html]("http://membres.lycos.fr/sethnakht/FAQ%20MediaPlayerConnectivity.html")
este link lo saque del about del plugin espero les sirva (lo saque del foro de ubuntu en ingles)

PD no es un plugin sino una extencion del browser

saludos

Excelente ! Gracias.

---

### Post by sdm_cacto on 2006-12-21
Ya que estamos existe alguna pagina con las radios mas importantes de argentina?? o de Bs As por lo menos??

---

### Post by spg76 on 2006-12-21
> **sdm_cacto said:**
> Ya que estamos existe alguna pagina con las radios mas importantes de argentina?? o de Bs As por lo menos??

Podes probar con [http://www.cxnlive.com/ar/](http://www.cxnlive.com/ar/). No solo hay radios; también hay Canales de TV y Diarios.

---

### Post by marianom on 2006-12-21
Yo he intentado este metodo con Continental porque necesito escuchar si o si el programa de Dolina todas las noches pero he sido humillado en repetidas ocasiones. Voy a probar lo que sugieren a ver si me salte algun paso.

---

### Post by elgatogordo on 2006-12-21
funciona pero necesitas un reproductor que lea asx como el kaffeine o el vlc

---

### Post by marianom on 2006-12-21
Entonces si instalo alguno de los dos que mencionas (cual es el mas liviano? pienso usarlo solo para ese tema en particular porque ya me acostumbre al rhythmbox), sin adicionales podre escuchar el programa?

---

### Post by elgatogordo on 2006-12-21
> **marianom said:**
> Entonces si instalo alguno de los dos que mencionas (cual es el mas liviano? pienso usarlo solo para ese tema en particular porque ya me acostumbre al rhythmbox), sin adicionales podre escuchar el programa?

No tenés que instalar nada, acabo de encontrar el mms para escuchar continental en el rhythmbox. en la ventana de agregar nueva radio pega esto
mms://66.175.96.10/arcontinental%3FMSWMExt
despues contame

---

### Post by spg76 on 2006-12-21
> **marianom said:**
> Yo he intentado este metodo con Continental porque necesito escuchar si o si el programa de Dolina todas las noches pero he sido humillado en repetidas ocasiones..

Mariano,  Dolina no está más en Radio Continental. Ahora va a salir por Radio 10 (AM 710). Si, por Radio 10, aunque usted no lo crea. Creo que empieza en enero.

---

### Post by scrooge_74 on 2006-12-21
> **sdm_cacto said:**
> Ya que estamos existe alguna pagina con las radios mas importantes de argentina?? o de Bs As por lo menos??

No sé si salen las de argentina, pero si instalas el streamtuner, tienes la lista de todas las emisoras por internet

---

### Post by felipelerena on 2006-12-22
por consola:
```
mplayer la-direccion-de-la-radio
```

---

### Post by marianom on 2006-12-23
elgatogordo: cuando en el rhythmbox pongo la dirección me tira *No hay un manejador de URI implementado para «mmsh»/«mms»*. Me pasa tanto en continental como en Radio 10 (¡el horror! ¡el horror!). ¿Sabés como puedo zafarla?

spg76: tenía la leve sospecha y se ha cumplido... de solo ver las caripelas que salen en la programación de radio10 me asusto... pero bue, 12 años escuchando todas las noches el mismo programa no van a cambiar así nomás. Ultimamente estaba un poco rebelde por el tema que en Córdoba el programa no sale al aire, así que no lo estaba escuchando.


Gracias por los comentarios y la ayuda.

---

### Post by elgatogordo on 2006-12-23
que no panda el cunico lo que tenes que hacer es esto
1) bajate e instala automatix [www.getautomatix.com](www.getautomatix.com)
2) abrilo, lo tenes en APLICaCIONES HERRAMIENTAS DEL SISTEMA
3) en el apartado multimedia selecciona los multimedia codecs e instalalos

---

### Post by marianom on 2006-12-23
Hay que hacerle al automatix nomás? Esa parte me la perdí... De todos modos Automatix me cae mal, eso que se meta con el source.list me rompe soberaramente (por más que después los vuelvo atrás al toque).

Voy a hacer el tiro a ver que sale, la ultima vez que usé Automatix con el Rhythmbox no me andaba la radio. Gracias por el tip elgatogordo.

---

### Post by elgatogordo on 2006-12-23
> **marianom said:**
> Hay que hacerle al automatix nomás? Esa parte me la perdí... De todos modos Automatix me cae mal, eso que se meta con el source.list me rompe soberaramente (por más que después los vuelvo atrás al toque).

Voy a hacer el tiro a ver que sale, la ultima vez que usé Automatix con el Rhythmbox no me andaba la radio. Gracias por el tip elgatogordo.

instalalo, instalate los codecs y despues desinstalas automatix desde el sinaptic

---

### Post by augustose on 2008-05-07
Estimado Sebastian, quisiera saber si estas pudiendo ver cxnlive en ubuntu.
Yo no estoy pudiendo ver los canales que piden clave. 
tengo ubuntu 8.04 y Firefox 3 b5 en el cual no funciona el 
[http://membres.lycos.fr/sethnakht/FAQ%20MediaPlayerConnectivity.html](http://membres.lycos.fr/sethnakht/FAQ%20MediaPlayerConnectivity.html)

Desde ya muchas gracias por cualquier aporte que puedas hacer,
Saludos cordiales 
Augusto

---

### Post by lu9uol on 2008-05-07
Hola, soy nuevo en el foro, asique me presento, Fernando de Macachin, La Pampa.
Con respecto a las radio encontre un link en el que hay muchas radios y con un formato que las acepta el Rhythmbox
[http://forums.screamer-radio.com/viewtopic.php?t=4641]("http://forums.screamer-radio.com/viewtopic.php?t=4641")
No se si lo conocian si esta repetido disculpas

---

