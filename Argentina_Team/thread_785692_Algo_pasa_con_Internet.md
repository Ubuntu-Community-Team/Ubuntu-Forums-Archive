---
title: "Algo pasa con Internet"
date: 2008-05-07
forum: Argentina Team
---

### Post by pol666 on 2008-05-07
Tengo un problemon...

Hpy prendo la PC todo joya, me baje wine.doors por que queria ver que tal era y cuando estaba actualizando se traba.. mato el proceso, lo abro otra vez y me tira este cartelito


[IMG]http://i32.tinypic.com/8xvqkg.jpg[/IMG]


Me fijo el icono de red y:

 [IMG]http://i31.tinypic.com/2ed5mkm.jpg[/IMG]

Abro firefox e internet tenia normalmente.. 

Pero me fije el screenlet del clima 

[IMG]http://i30.tinypic.com/9leqfa.jpg[/IMG]


:shock: Pongo el synaptyc  y baje cualquier cosa lo primero que vi fue el tux.paint...   Y bajaba. las luces del modem todo bien

Que pasa hay algo de la red que no me esta andando

lalala que falta de ortografia fea que tengo :lolflag:

---

### Post by atatiducken on 2008-05-07
yo tuve el mismo error, pasa que tengo conexion por arnet con el modem huawei por usb, y tuve q configurarlo, imagino que por eso no me lo detecta wine-doors, en la pag oficial habia varios con el mismo error, me fijo si lo solucionaron y vuelvo
saludos

P/D: coneccion es con x en los tags, conexion :D

---

### Post by pol666 on 2008-05-07
tengo internet por modem ethernet y me anduvo siempre el screen let :\ y el applet de red estaba activo

---

### Post by fgl82 on 2008-05-07
ME PASA LO MISMO CON EL SCREENLET DEL CLIMA!!! 

Qué cosa extraña!!!

---

### Post by pol666 on 2008-05-07
> **fgl82 said:**
> ME PASA LO MISMO CON EL SCREENLET DEL CLIMA!!! 

Qué cosa extraña!!!



puede ser que me hallan sucedido las 3 cosas esas por pura casualidad. y lo del screenlet sea un problema independiente de mi pc. Capas sucedio antes  y yo lo relacione todo junto. 

vere...

---

### Post by spg76 on 2008-05-07
Lo del Screenlet puede ser un problema diferente, teniendo en cuenta que el applet del clima de Awn también dejó de funcionar por un cambio que hizo Weather Channel.

---

### Post by sergiom99 on 2008-05-07
todos los cosos del clima "se rompieron" porque weather.com cambio el formato de sus feeds o algo por el estilo.
a mi me paso con el liquid weather para SuperKaramba.
aca explican como retocar LW>
[http://ubuntuforums.org/showthread.php?t=784669&highlight=liquid+weather](http://ubuntuforums.org/showthread.php?t=784669&highlight=liquid+weather)

---

### Post by fgl82 on 2008-05-07
Bárbaro, gracias por el link!

---

### Post by pol666 on 2008-05-07
Como es que hay que hacer?... no entendi ni jota lo del link

---

### Post by sergiom99 on 2008-05-07
explican como cambiar la configuracion del liquid weather, para KDE.
estoy tratando de hacerlo andar ahora... veremos que queda.

---

### Post by Hei Ku on 2008-05-07
click derecho sobre el liquid weather, configurar tema. Ahi tenes varias opciones. A mi me anda mejor usarlo con el accuweather para obtener los datos de buenos aires.

---

### Post by sergiom99 on 2008-05-07
el tema es que no es configuracion del LW sino del sitio de donde chupa el feed del clima. en el link al otro thread explica como actualizarlo para que siga funcionando.

---

### Post by pol666 on 2008-05-07
claa pero yo uso ClearWeather screenlet 8-)

---

### Post by sergiom99 on 2008-05-07
pol, 
aca explican como editar los archivos para que funcionen con los cambios de weather.com

[http://ubuntuforums.org/showthread.php?t=784053&highlight=clear+weather](http://ubuntuforums.org/showthread.php?t=784053&highlight=clear+weather)

espero te sirva/ Sergio

---

### Post by _kAz_ on 2008-05-08
Pregunto...

[SIZE="5"]¿¿¿A alguien ya le anduvo el weather applet de **AWN**???[/SIZE] 

Cuando quise hacer las modificaciones en weather.py fue para peor. Así que sigo esperando que se solucione solo por actulizacion o similar. Si alguno ya lo tiene funcional que diga como hizo.

Salu3.

---

### Post by pol666 on 2008-05-08
bueno agregue el &link=xoap en todas las URL y funciono a la perfeccion.

---

### Post by _kAz_ on 2008-05-08
> **pol666 said:**
> bueno agregue el &link=xoap en todas las URL y funciono a la perfeccion.

El archivo weather.py que modificaste en qué ubicación esta??? Yo modifique el de usr/lib/awn/applets/weather y salio para la mi****!!!

---

### Post by pol666 on 2008-05-08
**/usr/share/screenlets/ClearWeather.py**

Ese archivo edita no el que es .pyc !!!!!!!
Busca ..en dos lados dice "Xoap" y una sintaxis.. bueno donde esta la URL complicada buscas y copias eso &link=xoap

---

### Post by _kAz_ on 2008-05-08
> **pol666 said:**
> **/usr/share/screenlets/ClearWeather.py**

Ese archivo edita no el que es .pyc !!!!!!!
Busca ..en dos lados dice "Xoap" y una sintaxis.. bueno donde esta la URL complicada buscas y copias eso &link=xoap

Ahhhhh creo que estamos hablando dos cosas diferentes mi amigo... A vos te funca el SCREENLETS, yo necesito que me funcione el [SIZE="5"]AWN[/SIZE] pero yaaaaaa!!!! [-o<[-o<[-o<

Cuando quise modificar el weather.py se me fue todo al ***** y tuve que reinstalar los applets :(:(

Alguien que use AWN que me diga si ya funciona el weather applet o como hizo para que funcione!!!

---

### Post by spg76 on 2008-05-09
Ya arreglaron el applet del clima en Awn.
Saludos.

---

