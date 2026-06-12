---
title: "instalee ubuntuu"
date: 2007-11-19
forum: Argentina Team
---

### Post by fedeavila on 2007-11-19
buenas gentee!! como va?? 
hago este post xa informarles q en el dia de ayer acabo de instalar ubuntu 7.04 en mi compu
tras arduos intentos de particionar, bajarme el alternate y de ninguna manera poder instalarlo 
xq me tiraba un mensaje de error q x "causas desconocidas" no se habia podido efectuar el particionado
asi q decidi pasar todos mis documentos importantes a una compu q tengo en mi red domestica 
e instalar ubuntu POR COMPLETO en mi computadora
debo decir q la instalacion duro en total 4 LARGAS HORAS... pero las valio!
al no tener una aceleradora de video y mi escasa ram de 256 megas cargar el live cd se me hacia ETERNO
pero con mucha paciencia (y lo valio absolutamente) se pudo instalar este copado sistema operativo
basicamente, comparando con windows xp, es un poco mas veloz, parece mas estable, espero q realmente sea asi
no se cuelga, no se tilda (en el xp tampoco)
las aplicaciones, los metedos abreviados con el teclado son casi los mismos
el estilo visual es atractivo, suave
el sistema en si es bastante personalizable
con respecto a las aplicaciones q vienen pre-instaladas estan bastante bien, 
he verificado q trae (x ej) para hacer capturas de pantalla que en windows xp te tenias q bajar desde internet 
firefox, openoffice (q desgraciadamente esta en ingles), el gimp q seria (eso dicen) como un sustituto del photoshop; 
gaim para reemplazar al MALISIMO windows live messenger, entre otros
algo q me llamo la atencion es la "Carpeta Personal" q asumo q sera algo asi como Mis documentos
espero q asi lo sea xq en ese directorio puse Mis fotos, Mi musica, Mis videos, etc, etc, etc
me di cuenta tambien q no necesito configurar nada, tengo servicio de Internet desde la otra pc, 
puedo tambien acceder a sus Docs escribiendo la ruta "smb://usuario/mis documentos/" 
lo malo es q desde la otra pc no se puede acceder a la mia
no aparece mi compu por ningun lado, es como q esta invisible, igual supongo xq no esta activado Carpetas Compartidas, 
lo que sucede es q un par de aplicaciones necesitaron descargarse de internet y mi ***** Speedy no me lo permite xq se corta la conexion cada 2x3
por razones q desconozco y q Telefonica tambien desconoce (ja!) ¬¬
ah! cierto! los simbolos !"·$%&/()=?¿Ç* 
funcionan TODOS, c/u ubicado donde tiene q estar, tal y como aparece en el mismo teclado
cuando apago y enciendo la compu, se inicia mas rapido q windows xp, alrededor de 4 minutos, y ya esta lista para ser "tocada" jaja..
la utilidad de los multiples escritorios tambien es algo ideal aunq ya lo conocia, 
yo x ej tengo un desktop q se llama "*****" y otro q se llama "internet" y x su nombre, su utilidad..

bueno la verdad ya no me queda mucho x decir.. 
aca pongo una captura de pantalla xa q vean como quedo 
y al lado el bloc de notas (o gedit) de lo q voy escribiendo.

un saludo!! :D

fede




p/d: acabo de darme cuenta q no se escucha el sonido cuando pongo algun videito desde youtube... 
alguien sabe a q se debe? codecs ya los tengo... 
escucho musik y veo pelos de la compuucha

p/d2: alguien sabe como poner las fuentes de windows? tipo comic sans o verdana... 
xq las q hay aca ni se parecen...

p/d3: ya pude arreglar lo de carpetas compartidas!! :D

p/d4: disculpen la falta de signos de puntuacion, el prox post lo hago con mas tiempo

abajo el screenshoot...

[IMG]http://img519.imageshack.us/img519/682/pantallazokh5.png[/IMG]

---

### Post by valucha on 2007-11-19
[COLOR="DarkOrchid"]Te felicito :). 
La verdad que fuiste muy valiente al haberte pasado.
Para ver los videos de youtube no sé cuál es el codec específico, pero yo instalé todos los que se llamaban "gstreamer" así me olvidaba de andar bajando codecs.


Te recomiendo algunos programas que yo uso para que vayas probando:
Mensajero: "emesene" MUUUUY liviano y soporta el 99% de todas las funciones del MSN messenger incluidas las cosas del Plus... PERO no permite la transferencia de archivos. Yo uso el mail, pero bueno, para mi es el mejor mensajero lejos.

Browser: Opera es muy bueno para compu con bajos recursos. EL firefox es demasiado robusto.

Office: gnome office, viene con el gnumeric, abiword entre otros son muuy livianos y útiles: Desventaja: el Abiword no tiene barra de dibujo (no podes hacer cuadrados, flechas y todo eso).

Reproductor de peliculas: Xine.
"                 de música: Yo uso el Rhythmbox porque soporta muy bien mi iPod. Pero cuando tenía una compu más vieja usaba el Exaile! que es re livianito.


[COLOR="DarkOrchid"]
Ah ah me olvidaba,,, acá [http://ubuntu.wordpress.com/2005/09/09/installing-microsoft-fonts/](http://ubuntu.wordpress.com/2005/09/09/installing-microsoft-fonts/) te enseñan a instalar las fuentes de M$$[/COLOR]


Espero que te sirva. Saludos.[/COLOR]

---

### Post by juanman on 2007-11-20
Para el OpenOffice en español: instalá desde synaptic los paquetes openoffice.org-help-es y openoffice.org-l10n-es
O si querés, podes instalarlo desde consola escribiendo: 
sudo aptitude install openoffice.org-l10n-es openoffice.org-help-es

Para el tema del youtube sin sonido... hay gente q lo solucionó con:
1) Escribi en consola o apretá alt + f2: sudo gedit /etc/firefox/firefoxrc 
2) Poné FIREFOX_DSP=&#8221;esd&#8221; , donde pone FIREFOX_DSP=&#8221;none&#8221;
3) Guardá el archivo y reiniciá Firefox

Si no anda probá instalando con synaptic: libxine-extracodecs y totem-xine

Contá como te fue...

---

### Post by tzulberti on 2007-11-20
Lo de las fuentes de Windows (Times New Roman, etc..) se solucionan instalando el paquete msttocrefonts (no me acuerdo si se escribia exactamente asi, pero es algo similar).

---

### Post by fscodelaro on 2007-11-20
Lo que a veces conviene es instalar el paquete de restricted extras:

```
sudo apt-get install ubuntu-restricted-extras
```

que trae las fuentes de microsoft, java, codecs para mp3 y streaming audio / video y no se que mas, en un conveniente meta-paquete.

---

### Post by fedeavila on 2007-11-23
> **valucha said:**
> [COLOR="DarkOrchid"]Te felicito :). 
La verdad que fuiste muy valiente al haberte pasado.
Para ver los videos de youtube no sé cuál es el codec específico, pero yo instalé todos los que se llamaban "gstreamer" así me olvidaba de andar bajando codecs.


Te recomiendo algunos programas que yo uso para que vayas probando:
Mensajero: "emesene" MUUUUY liviano y soporta el 99% de todas las funciones del MSN messenger incluidas las cosas del Plus... PERO no permite la transferencia de archivos. Yo uso el mail, pero bueno, para mi es el mejor mensajero lejos.

Browser: Opera es muy bueno para compu con bajos recursos. EL firefox es demasiado robusto.

Office: gnome office, viene con el gnumeric, abiword entre otros son muuy livianos y útiles: Desventaja: el Abiword no tiene barra de dibujo (no podes hacer cuadrados, flechas y todo eso).

Reproductor de peliculas: Xine.
"                 de música: Yo uso el Rhythmbox porque soporta muy bien mi iPod. Pero cuando tenía una compu más vieja usaba el Exaile! que es re livianito.


[COLOR="DarkOrchid"]
Ah ah me olvidaba,,, acá [http://ubuntu.wordpress.com/2005/09/09/installing-microsoft-fonts/](http://ubuntu.wordpress.com/2005/09/09/installing-microsoft-fonts/) te enseñan a instalar las fuentes de M$$[/COLOR]


Espero que te sirva. Saludos.[/COLOR]

gracias por las felicitaciones!!
con respecto a lo de gstreamer ahora mismo me dispongo a instalarlo
el emesene esta muy piola! lastima q lo tengo q ejectuar desde una carpeta q yo mismo cree q se llama "mis programas" adentro de carpeta personal y siempre me pregunta q si kiero "ejecutar" el archivo o abrirlo con el gedit, con respecto a lo del envio de archivos me da =
despues, el firefox no solo es para mi el mejor navegador sino el unico q utilice toda mi vida y estoy acostumbrado a usar, en mi compu funciona perfectamente por suerte
con respecto a lo de las fuentes de microsoft ya las pude instalar!! kedo todo completito aunq me gusta mas Sans, pero me di cuenta q "los demas" al yo usar esta fuente, ellos ven mi letra como una feita y flaquita jajaja no me importa.

muchas gracias por toda la informacion che! no sabes como me ayudaste! te lo agradezco

---

### Post by fedeavila on 2007-11-23
> **juanman said:**
> Para el OpenOffice en español: instalá desde synaptic los paquetes openoffice.org-help-es y openoffice.org-l10n-es
O si querés, podes instalarlo desde consola escribiendo: 
sudo aptitude install openoffice.org-l10n-es openoffice.org-help-es

Para el tema del youtube sin sonido... hay gente q lo solucionó con:
1) Escribi en consola o apretá alt + f2: sudo gedit /etc/firefox/firefoxrc 
2) Poné FIREFOX_DSP=&#8221;esd&#8221; , donde pone FIREFOX_DSP=&#8221;none&#8221;
3) Guardá el archivo y reiniciá Firefox

Si no anda probá instalando con synaptic: libxine-extracodecs y totem-xine

Contá como te fue...

holas!! primero muchas gracias por la info como a la chica q tb me ayudo
con lo de openoffice.org-help-es y openoffice.org-l10n-es lo pude instalar re bien!!
buenisimo!!
con respecto a lo de firefox te cuento q hice todo exactamente como me explicaste
pero cuando le cambie esa letra, cerre, reinicie, y firefox recontra murio
jajaj
me decia "iniciando firefox" pero al cabo de unos segundos se cerraba la ventanita.
asi q agarre y lo tuve q desinstalar y volver a instalar desde synaptic y ya fuee que kede asi...
ahora toy probando lo de libxine espero q funcione sino ya fue q kede como esta
muchas gracias!!!

lo q toy haciendo ahora son dos cosas, primero instalar el wine para usar photoshop (si logro hacerlo) porque el photoshop tiene una herramienta q el gimp no tiene q es la "curita" q es como una especie de pincel clonador pero q ademas como q disuelve un pokito la imagen q yo la utilizo para borrar granitos jjaa o marcas o cosas asi en un rostro q el clonador no sirve, cosa q tampoco es fundamental xq puedo hacerlo desde la otra compu en red q tengo...
ah y eso!! la red anda al 50%, porque yo puedo entrar a la compu con windows pero la q tiene windows no puede a la mia, y ya instale el coso ese de samba, bla bla

ahora tambien toy intentando instalar el frostwire q dicen q es el sustituto del ares, pero me tengo q bajar JAVA y me lo bajo y no lo puedo ejecutar (o hacer funcionar) la verdad ya ni se como se dice jaja

un saludo!! sos el master del ubuntu!! :D

---

### Post by ubuntu27 on 2007-11-23
Para isntalar Java yFormatos restringidos. Abre el terminal que se enceuntra en el menu Aplicaciones/Accesorios/Terminal

y copia y pegal lo siguiente:

```
sudo apt-get install ubuntu-restricted-extras
```

Eso bajara y isntalara automaticamente Java, mp3, wmv, fuentes, et cetera.

---

### Post by juanman on 2007-11-24
> **fedeavila said:**
> 
ahora tambien toy intentando instalar el frostwire q dicen q es el sustituto del ares, pero me tengo q bajar JAVA y me lo bajo y no lo puedo ejecutar (o hacer funcionar) la verdad ya ni se como se dice jaja


Me parece q no te conviene el Frostwire xq te va a andar lento en tu pc (está hecho en java q es pesado para cargar). Podes usar el Ares via wine q anda muy bien (salvo las previsualizaciones) o usar la red de Ares via Gift: [aca hay un tuto]("http://120linux.com/ares-en-pinguino-sin-necesidad-de-wine/") pero es medio tedioso seguirlo. En realidad, ese tuto se puede simplificar instalando el paso 1 y el 3 por synaptic (no es necesario compilar). Cuando tenga tiempo voy a hacer un paquete todo en uno con la instalacion simplificada...

---

### Post by valucha on 2007-11-24
> **fedeavila said:**
> gracias por las felicitaciones!!
con respecto a lo de gstreamer ahora mismo me dispongo a instalarlo
el emesene esta muy piola!** lastima q lo tengo q ejectuar desde una carpeta q yo mismo cree q se llama "mis programas" adentro de carpeta personal y siempre me pregunta q si kiero "ejecutar" el archivo o abrirlo con el gedit, con respecto a lo del envio de archivos me da =**
despues, el firefox no solo es para mi el mejor navegador sino el unico q utilice toda mi vida y estoy acostumbrado a usar, en mi compu funciona perfectamente por suerte
con respecto a lo de las fuentes de microsoft ya las pude instalar!! kedo todo completito aunq me gusta mas Sans, pero me di cuenta q "los demas" al yo usar esta fuente, ellos ven mi letra como una feita y flaquita jajaja no me importa.

muchas gracias por toda la informacion che! no sabes como me ayudaste! te lo agradezco
[COLOR="DarkOrchid"]

AH????,.. yo lo ejecuto desde Aplicaciones-Internet,
¿Cómo lo instalaste?, probaste el deb? (los instaladores de Debian y, por lo tanto, de Uubuntu?.
Bajátelo de [acá]("http://www.getdeb.net/app.php?name=emesene")

Y de paso te voy dando la data de que esa página es excelente :).

SaLUDOS.[/COLOR]

---

### Post by Mauro22 on 2007-11-24
Para ejecutar el emesene, solo basta con:

```
python /usr/share/emesene/controller.py
```

---

