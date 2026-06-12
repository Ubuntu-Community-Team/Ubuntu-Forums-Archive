---
title: "COMO: Counter Strike 1.6 NO-STEAM en UBUNTU"
date: 2007-08-23
forum: Argentina Team
---

### Post by User21 on 2007-08-23
**COMO: Counter Strike 1.6 NO-STEAM en Ubuntu.**

**Introducción:** De entrada, se supone que gran variedad de programas son ejecutables sin problemas por Wine, e incluso algunos aseguran que allí, los programas corren mejor o mas estables que en su sistema operativo nativo (entiéndase Micro$oft WinSucks). En mi caso, **Counter Strike 1.6** funciona de lujo, y puedo jugarle en los servers de Internet, además. Esto no significa que sea infalible: a algunas personas aún no les funciona!!! A continuación, un** cómo** según mi experiencia en su instalación:

**PC usado:** AMD Sempron 1.75 GHz - 512 Mb RAM - Vídeo GeForce mx 4000 de 64 MB. Claramente esta pc supera los requerimientos mínimos del CS 1.6 .
**SO**: Ubuntu 7.04 Feisty Fawn + Wine 0.9.33  (la actual a la fecha de éste cómo: 23/08/07)
 

 **Recomendaciones:** tener las actualizaciones de Ubuntu y Wine al día. **ES OBLIGATORIA LA NECESIDAD de aceleración 3D** de tu tarjeta de vídeo (como se logra? puedes verlo en otros tutoriales, esto es solo para CS 1.6.)
 

 **1)** Bajarse los archivos necesarios para correr Counter Strike, de la misma forma en que lo harías en Wine2. 

__El instalador NOSTEAM v23B pesa algo 250 MB aprox. Con esto es suficiente, pero si deseas, puedes bajarte el parche de la version 26__, el cual se instala encima (yo estoy usando la 23B). 
Si no sabes como conseguirlo, pidelo mediante MP.

**Tahoma.ttf**  : La fuente TrueType necesaria para visualizar los diálogos del juego. Obtenla [URL="http://www.filesearching.com/cgi-bin/s?q=tahoma.ttf&s1=255000"][B]Aqui.
[/B][/URL]
Al finalizar la instalación, Wine te pedira instalar **Gecko**: browser por defecto necesario para visualizar contenido HTML en el juego. Gecko se te pedirá ser instalado automáticamente si antes no lo habías instalado, y es OBLIGATORIO para el normal desarrollo del juego (requiere conexión a internet).  
 

 **2)** Copiate la fuente Tahoma en el directorio:
** /home/USUARIO/.wine/drive_c/windows/fonts** .
De esta forma, CS buscara la fuente allí.

**3)** Una vez bajado el instalador, pues instálalo: ingresa al directorio donde lo descargaste y ejecutalo vía wine, en un terminal:
```

cd /directorio/donde/descargas
 wine 'CS1.6.Fullv23B.exe'  

```(o como se llame tu instalador).
 
La instalación se muestra tal cual lo haría en M$. Dejalo instalar.
 

 4) Una vez finalizada la instalación, crea en el escritorio, en un panel o donde desees, el enlace hacia el. La ruta de ejecución sera de acuerdo a tu instalador; en mi caso es algo así:


 **wine '/home/USUARIO/.wine/drive_c/Archivos de programa/Counter-Strike 1.6/hl.exe' -game cstrike -window** 


 Especial atención en los apóstrofos antes y después de la ruta, y los modificadores finales -game y -window- Estos le indican al HL.exe que deseas ejecutar el Counter Strike y en una ventana (opcional). Hay varios modificadores de este tipo, y los familiarizados con CS los conocen.
 Elige un buen PNG o ICO para tu enlace y LISTO. Con solo doble clic, deberías estar entrando al juego! Al iniciar una partida, si no lo tenias, SE TE PEDIRA INSTALAR GECKO por unica vez. Aceptar!
 
 **Espero logres hacerlo correr y diviertete!!!**
[B]
NOTAS FINALES:[/B] 
Wine, por defecto, me eligió el servidor de sonido OSS y funciona de maravillas. Si tienes problemas con el audio, puedes cambiar las opciones, tipeando en una consola ***winecfg*** (con el juego cerrado, obvio). 
Es necesaria la compatibilidad WindowsXP, puedes activarla en la pestaña Aplicaciones de la configuración de Wine (**winecfg). ** 
 Personalmente recomiendo jugar a pantalla completa, pero puedes correrlo en ventanas: en mi pc he sufrido algunos bugs al intentar pasar al Pidgin o amsn, mientras juego. 
Todo lo que necesites saber acerca del JUEGO, no lo preguntes aqui. HAY MILLONES DE PAGINAS dedicadas a Counter Strike. ;)

---

### Post by User21 on 2007-08-23
Un bug conocido es que al jugar CS 1,6 en Ubuntu, **el CS pierde el control del mouse al hacer ALT TAB!** No he encontrado una solucion. Lo que hago es simplemente apretar escape en el juego, para ver el menu, y recien alli, pasarme a alguna otra aplicacion.
Si alguien obtiene como cambiarlo, nos informaaa!! u_U

**Y NO, TAMPOCO FUNCIONA EL anticheat SXE Injected ! u_U**

---

### Post by msangil on 2007-08-25
Me mataste. Estaba a punto de empezar a instalar y leí el último comentario sobre el Anti-cheat.

El 90% de los servidores argentinos que valen la pena obligan a usar el programa ese.

Capaz estas mismas instrucciones pueden aplicarse a otros juegos. Revisaron ya la lista de juegos probados compatibles con el Wine? Hay unos cuantos grossos.

---

### Post by Mauro22 on 2007-08-25
Excelente, corre de maravillas..


Lastima que estoy fuera de practica :(:(

---

### Post by kannon345 on 2008-02-07
tengo algunas dudas y problemitas acerca de esto:

1. tengo problemas con el audio: me sale algo asi cuando entro a la pestaña de sonido en en winecfg

```

ALSA lib conf.c:3939:(snd_config_expand) Unknown parameters 0
ALSA lib control.c:910:(snd_ctl_open_noupdate) Invalid CTL default:0
ALSA lib seq_hw.c:457:(snd_seq_hw_open) open /dev/snd/seq failed: No existe el fichero ó directorio
fixme:jack:JACK_drvLoad error loading the jack library libjack.so, please install this library to use jack
ALSA lib conf.c:3939:(snd_config_expand) Unknown parameters 0
ALSA lib control.c:910:(snd_ctl_open_noupdate) Invalid CTL default:0
ALSA lib seq_hw.c:457:(snd_seq_hw_open) open /dev/snd/seq failed: No existe el fichero ó directorio

```

supongo yo que no esta instalado bien las librerias o algo asi.

2. Cuando ingreso al cs ( sin sonido) carga bien todo, pero justo cuando va aparecer el mapa se cierra la ventana.

3. El juego carga en una pequeña ventana, como hago para que sea FullScreen?

4. Estos pasos se podrian hacer tambien para ejecutar el hlds?

Espero me respondan, recien empiezo con esto del wine :D

---

### Post by User21 on 2008-02-07
1) En la config de WINE (winecfg desde una terminal) intenta utilizar OSS o instala las librerias de JACK (sudo apt-get install libjack0) o buscalas via Synaptic.

2) Del enlace o acceso directo al juego, elimina el modificador -window o en las opciones del juego destilda la opcion Run in a window, bajo la solapa "VIDEO" ; de este modo , el juego correrà en FULLSCREEN.
·
3) He leido que el HLDS funciona sin problemas, aunque personalmente no lo he corrido. Solo haz un enlace similar al del CS pero el ejecutable sería el HLDS. 
De todas formas, existe el servidor dedicado que corre bajo LINUX y esta disponible en la pagina de Steam, gratis y listo para instalar., aunque requiere que leas un poco como instalarlo, en el mismo sitio. Ese si lo he probado y es totalmente funcional, estable y manejable via consola. Es el que usan los servidores de CS como Clanco, Area51 o 3DGames.

Ojala eso os ayude un poco.

---

### Post by nemodot on 2008-02-07
No sé si le pasa a alguien más, pero no puedo instalar Gecko, simplemente no se instala, se queda ahi colgado y no pasa nada.

Tambien me lo pide cuando uso el ares, por que tiene un navegador, pero se queda ahi y no progresa la instalación. Alguien sabe como solucionarlo?

---

### Post by User21 on 2008-02-07
Con solo buscar e instalar Gecko via Synaptic, creo que deberias salir andando... aunque a mi siempre me funcionó.... lo chequeo al llegar a mi casa...

---

### Post by nemodot on 2008-02-07
No la encuentro el en synaptic, encontré unas librerias que estaban relacionadas, las instale pero el problema persiste.

---

### Post by User21 on 2008-02-07
Encontre [esto]("http://genlinux.wordpress.com/2007/12/31/gowto-instalando-el-modulo-gecko-para-wine/"): no lo he testeado. Suerte!

---

### Post by kannon345 on 2008-02-08
gracias por la respuesta.

Bueno creo que ya he solucionado lo del sonido usando el OSS.

Tambien lo de la ventana, le kite el -window pero seguia, lo solucione destildando la opcion en el juego mismo como recomendaste.

Pero aun tengo un problema, el mas serio creo yo, ya estoy con sonido, fullscreen y todo carga normal, pero cuando termina la barra verda con amarilla y pasa al mapa mismo, se me cierra el juego. No tengo ni idea que puede ser esto. Espero que me puedan recomendar una solucion

Con respecto al hlds lo voy a probar despues que solucione esto :P

gracias.

---

### Post by User21 on 2008-02-09
A mi no me sucede esto. Tienes aceleración 3D, antes que nada ???
La consola devuelve algún mensaje ???

---

### Post by nemodot on 2008-02-09
Acá les adjunto a modo de attach, el logo png que uso para el icono del Counter Strike 1.6 en mi PC.

Saludos!

---

### Post by faktorqm on 2008-02-11
Estuvimos averiguando con User21, FreeDownload, Juan o como se llame sobre el sXe Injected, y no hay caso, jamás va a funcionar bajo GNU/Linux, por que al igual que programas "themers" del estilo del style XP y esas cosas utiliza directamente el kernel de windows para funcionar, por lo tanto no depende tanto de las dll's sino ya mas a nivel operativo. Voy a ver si le pregunto a los desarrolladores a ver que onda en intentar migrar (algo?) salu2!

---

### Post by pol666 on 2008-02-16
si todo muy lindo, lo hice cuando al poco tiempo de instalar ubuntu pero el sXe  
es todo para los server :S

---

### Post by qntal on 2008-02-17
No me molestaría comprar un half life original para jugar por steam, pero el tema es que acá en argentina todo el mundo juega la no-steam con injected... no queda otra mas que tener una partición con windoze.

El Counter-Strike Source lo probaron? se juega sin anti-cheat.

---

### Post by faktorqm on 2008-02-18
Nosotros levantamos un servidor de CS source en un linux una vez que armamos una lan en la casa de un amigo para no usar una pc de servidor, pero el cliente lo usamos desde windows. no se si por que el pibe que lo instalo no tenia ganas de instalarle a todos los que usaban linux el cs source o si por que no andaba. Encima cero ganas de instalarlo aajja salu2!

---

### Post by azhtar on 2008-03-06
creo que te sales de las normas de los foros de ubuntu al hacer un how to promocionando uso de software pirata o ilegal, ya que de entrada es ilegal omitir el uso de steam para cualquier juego de valve

---

