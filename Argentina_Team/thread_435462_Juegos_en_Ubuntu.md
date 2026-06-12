---
title: "Juegos en Ubuntu"
date: 2007-05-06
forum: Argentina Team
---

### Post by lugonesjoaquin on 2007-05-06
Vamos a comenzar un post donde cada uno postee un juego (o más) que haya probado en Gnu/Linux y que quieran recomendarlo.

Comienzo yo
[B]
OpenArena[/B]

Uno de los pocos que he probado e impresionante. Basado en la liberacion del motor de Quake 3, con graficos y sonidos mejorados, sale OpenArena.
Lamentablemte no es compatible con el original por lo que muchos mods pueden no andar.

[ScreenShot]("http://scr.softonic.com/s2/61000/61524/3_water_52714.jpg")

No se si se encontrará ya en los repositorios de Ubuntu pero la ultima version que probé de UBuntu no la tenia. Por lo que aqui esta el Deb:

> [http://ftp.pl.debian.org/debian/pool/main/o/openarena/openarena_0.6.0-2_i386.deb](http://ftp.pl.debian.org/debian/pool/main/o/openarena/openarena_0.6.0-2_i386.deb)

SIgan Ustedes..:P

---

### Post by scrooge_74 on 2007-05-06
Buen juego entretiene bastante

---

### Post by marianom on 2007-05-06
Yo detesto ese "4 en raya" que viene por defecto. Nunca le he podido ganar y siempre que invito a alguno a que lo juegue, lo ganan en la primera partida. No me gusta que mi zonsera sea tan evidente.

Cuando estoy aburrido juego un poco al doom que está en los repos (lxdoom o prboom) solo para recordar mi adolescencia (si alguien sabe donde puedo conseguir niveles nuevos para jugar, agradecido).

---

### Post by fetova on 2007-05-07
Pues yo recomiendo Battle for Wesnoth, no me acuerdo que estaba buscando en el foro y me encontre con que recomendaban el juego... muy bueno :D aunque algo compicado... la campaña de A Griffin's Tale o algo asi no encuentro como matar a los cuatro lizard siendo solo uno :( Pero bueno... las campañas en el synaptic son muy buenas y mas jugables

el paquete esta en repos y es wesnoth ;)

---

### Post by MeduZa on 2007-05-07
hola a todos, aca un experto en el tema (creo q soy el unico gamer de linux -.- )
puse en rojo los que recomiendo
juegos q jugue/o con wine: 

[COLOR="Red"]Warcraft 3 TFT[/COLOR] anda mejor q en windows
[COLOR="Red"]Heroes of might and magic V[/COLOR] anda bien con algunos detalles pero nada grave
[COLOR="Red"]HalfLife 2[/COLOR]: anda muy buen solo que el reflejo del agua a veces se ve en el cielo
RailRoad Tycoon 3: todo perfecto, a veces hace un titileo el piso pero nada grabe
[COLOR="Red"]The Settlers 4[/COLOR]: todo perfecto
[COLOR="Red"]Quake 4[/COLOR]: funciona perfecto
OurRuners: anda perfecto

juegos que jugue/o nativos de linux:
[COLOR="Red"]Neverwinter Nights[/COLOR]: anda perfecto y corre nativo de linux o desde wine (aunque no probe)
[COLOR="Red"]Frozen Bubble[/COLOR]: muy adictivo sobre todo online
[COLOR="Red"]Scorched 3d[/COLOR]: el clasico de DOS pero en 3d y muy mejodado, ademas podes jugar en internet esta pasado de bueno
[COLOR="Red"]Battle for Wesnoth[/COLOR] como dicen arriba muy adictivo :)

creo q por ahora esos son todos los que recuerdo
dos juegos q no pude hacer andar son: oblivion (no me puse aun)
y el Lineage 2 q para hacerlo andar no entiendo que hay q hacer
Saludos

---

### Post by QUASAR_FREAK on 2007-05-07
Creo que el Lineage 2 anda con wine hasta el C3, del C4 en adelante no anda gracias al gameguard.

** Nativos y Free:**

[Nexuiz]("http://www.alientrap.org/nexuiz/"): Juego de tiros al estilo Quake2 Mp pero con graficos mucho mas modernos (excepto los modelos de los players, que son horribles)
[URL="http://tremulous.net/"]
Tremolous[/URL]: Juego basado en el engine Quake 3, multiplayer.

[Cube Engine 1 y 2]("http://cubeengine.com/")

[Warsow]("http://www.warsow.net/")

** Nativos y comerciales:**

UT99 y UT2004

Quake 1, 2, 3 y 4

Doom 1, 2 y 3

** Emulados:**

Battlefield 2 

Battlefield 2142

Half Life 1 y 2

Counter Strike Source

Day of Defeat Source

Call of Duty 1 y 2

GTA 1, 2 y 3 (+expansiones)

Splinter Cell (solo jugue el 1)

Si me acuerdo de algun otro juego que haya disfrutado desde linux posteo =)

---

### Post by MeduZa on 2007-05-07
> **QUASAR_FREAK said:**
> Creo que el Lineage 2 anda con wine hasta el C3, del C4 en adelante no anda gracias al gameguard.


solo voy a jugar en un servidor de argentina donde juegan mis amigos asi que no me interesa el gameguards ya q no lo usan, usan un server free o algo asi


Por otro lado y yo q me creia el unico :) ya tengo un amigo en el foro :popcorn: 

el l2 nunca entendi como hacerlo andar y si me pegan el listado q sale en winehq (que ya me lo pasaron 10 veces) capas q haga la pregunta de porque no entiendo

---

### Post by undiaperfecto on 2007-05-07
me instale open arena, nunca se me habia ocurrido jugar en linux, esta bueno jajaja.
no soy de jugar en la pc, no me gusta, prefiero la play, pero esta bueno en linux, no se, te da la sensacion de que si lograste hacerlo funcionar sos groso. por mas que este en los repositorios y sea facilisimo instalarlo.

---

### Post by zspikes on 2007-05-07
[SIZE="3"]supertux[/SIZE]
q buen juego por favor, como lo amo!!! jaja, mario bros version linux!
```
sudo apt-get install supertux
```

[SIZE="3"]frozen bubble[/SIZE]
bubble blaster version linux tb, muy enviciante, para pasar los dias de lluvia jaja
```
sudo apt-get install frozen-bubble
```

[SIZE="3"]scorched 3D[/SIZE]
onda worms, pero con tanques y en 3D, muy bueno!
```
sudo apt-get install scorched3d
gksudo gedit /usr/share/applications/scorched3d.desktop

    * Inserta las siguientes lineas en el nuevo fichero 

[Desktop Entry]
Name=Scorched 3D
Comment=A 3D Remake Of Scorched Earth
Exec=scorched3d
Icon=
Terminal=false
Type=Application
Categories=Application;Game;ArcadeGame;

    * Guarda el fichero editado
    * Aplicaciones -> Juegos -> Scorched 3D 
```

[SIZE="3"]tux racer[/SIZE]
muy entretenido, es de carreritas... se larga tux por una montaña helada, enviciante :)
```
sudo apt-get install planetpenguin-racer planetpenguin-racer-data planetpenguin-racer-extras
```

[SIZE="3"]TEG[/SIZE] (tenes empanadas graciela jaja)
El juego de mesa q todos conocemos
```
sudo apt-get install teg
```

este fue mi humilde aporte, un saludo!!!!!

---

### Post by DuckMan on 2007-05-07
che quasar como hiciste andar el gta 2!?!??! lo jugamos en el laburo pero tenemos q usar winchot =(

---

### Post by QUASAR_FREAK on 2007-05-07
con wine, acabo de probar la version de gta2 que te bajas de la pagina de rockstar y anda asi que bajate wine y dale para adelante.

---

### Post by DuckMan on 2007-05-08
yo no la probe, sorry por la ignorancia

pasa q un compañero de laburo *lavaramano* la probo e iba muuuy lento, probare!

---

### Post by jpmorelli on 2007-05-08
Desde User Linux para el mundo !!! Algunos juegos que están en desarrollo para Linux.

Nosferatu
[http://www.nosferatuthegame.com/]("http://www.nosferatuthegame.com/")

Open Outcast
[http://www.openoutcast.org/en_techdemos.php]("http://www.openoutcast.org/en_techdemos.php")

IMPRESIONANTE !!! Mis favoritos, no veo la hora que esté listo:
[http://wildfiregames.com/]("http://wildfiregames.com/")

Links sacados de la Revista Users Gnu/Linux n33, nota de Franco Rivero. Gracias Franco !!! :lolflag:

---

### Post by QUASAR_FREAK on 2007-05-08
otro emulado ke probe fue el penumbra, usando cedega.

---

### Post by jajajavi on 2007-05-12
> **MeduZa said:**
> hola a todos, aca un experto en el tema (creo q soy el unico gamer de linux -.- )
puse en rojo los que recomiendo
juegos q jugue/o con wine: 

[COLOR="Red"]Warcraft 3 TFT[/COLOR] anda mejor q en windows

Hola, instalé Warcraft III con wine pero me salta un CD-ROM drive error (Unable to locate your CD-ROM drive). Supongo no encuentra la forma de acceder al cd, aunque lo arranco desde el autoplay.exe del mismo. ¿Hay alguna forma de arreglarlo? Gracias.

---

### Post by MeduZa on 2007-05-12
> **jajajavi said:**
> Hola, instalé Warcraft III con wine pero me salta un CD-ROM drive error (Unable to locate your CD-ROM drive). Supongo no encuentra la forma de acceder al cd, aunque lo arranco desde el autoplay.exe del mismo. ¿Hay alguna forma de arreglarlo? Gracias.

creo que se repara entrando en winecfg y te vas a driver y creas una unidad q sea CD-ROM

si no funciona eso avisame q buscamos mas a fondo

---

### Post by jayflower on 2007-05-13
> **marianom said:**
> Yo detesto ese "4 en raya" que viene por defecto. Nunca le he podido ganar y siempre que invito a alguno a que lo juegue, lo ganan en la primera partida. No me gusta que mi zonsera sea tan evidente.

Cuando estoy aburrido juego un poco al doom que está en los repos (lxdoom o prboom) solo para recordar mi adolescencia (si alguien sabe donde puedo conseguir niveles nuevos para jugar, agradecido).

A mi me pasa lo mismo con el Sokoban, alguien pudo avanzar bastante en los niveles? estuve jugando tardes enteras los primeros 4 niveles y nada. Sin embargo mi primo le sacó el jugo en 10 minutos.
Recomendado el Gcompris para chicos. Me recuerda el Click

---

### Post by lavaramano on 2007-05-13
> **DuckMan said:**
> yo no la probe, sorry por la ignorancia

pasa q un compañero de laburo *lavaramano* la probo e iba muuuy lento, probare!

ahora que lo decis, en ese momento no tenia los drivers de nvidia en la maquina.
quizas habria que probar de nuevo ahora que si los instale ahi.

aunque al mismo tiempo, en mi casa con la placa ati y toda la gilada andando. tb me iba lento..

por otro lado, en el foro (?) o algo de crossover de codeweavers un chabon con slack 10 (creo) lo hizo funcionar.
dicho sea de paso en el servidor del trabajo esta el crossover en un .deb

habria que fijarse.


no se si algo lo aporto ya, pero el Battle For Wesnoth.. otro juego bastante lindo :lolflag:


btw!. alguien probo al freecraft? (Si, aparentemente sigue vivo en los repos de debian al menos.)

---

### Post by lavaramano on 2007-05-13
a pesar de que quasar haya posteado al doom 1 2 y 3.
esta tb el freedoom en los repositorios y el gtetritnet (creo que era asi el nombre), obviamente un clon de gtk del tetrinet

edit: para jugar con el freedoom tb hace falta otro mas que se llama 'prboom'

nada mas.

---

### Post by zspikes on 2007-05-13
otro aporte mas:
**airstrike**
sudo apt-get install airstrike

enviciante a full jaja

---

### Post by enzomatrix on 2007-05-14
**Frets on Fire** es un vicio.
Más cuando bajás canciones del Guitar Hero y te ponés a tratar de sacarlas.
Es un emulador de guitarra.

[http://fretsonfire.sourceforge.net/](http://fretsonfire.sourceforge.net/)

---

### Post by Nemesis Teufel on 2007-05-16
Prueben el GL-117
Simulador de vuelo de guerra muy facil de jugar y bien hecho.
Esta en añadir y quitar programas.

---

### Post by scrooge_74 on 2007-05-17
> **Nemesis Teufel said:**
> Prueben el GL-117
Simulador de vuelo de guerra muy facil de jugar y bien hecho.
Esta en añadir y quitar programas.

Esto es criminal, ya me había hecho la idea de no poder jugar en Linux y que iba tener que usar mi PC sólo para trabajar........arrrghhhhh.......ahora tengo algo en que desperdiciar mi tiempo 


:lolflag:

---

### Post by Mafber on 2007-05-17
Hola, tienen otra alternativa... probar con un emulador de play (ej. epsxe) ;)

---

### Post by jajajavi on 2007-05-17
> **MeduZa said:**
> creo que se repara entrando en winecfg y te vas a driver y creas una unidad q sea CD-ROM

si no funciona eso avisame q buscamos mas a fondo

Tengo la unidad D: como /media/cdrom0 pero la cosa no funca.

---

### Post by Mafber on 2007-05-17
A mi me funciona, pero cargo las isos. 
probé el juego Raystorm. y funciona bien. lo unico que no pude hacer es maximice. Pero pude jugar bien
Le falta un poco más a emulado... pero por lo menos va tomando forma. :)


Edito: estoy jugando al Soul Blade y corre muy bien, los graficos no son tan fluidos como en windows pero acá me funciona con música durante las peles, cosa que no sabía que tenía :O

---

### Post by sebas.rhcp on 2007-05-17
El espxe2 para juegos de play2 viene muy bien

---

