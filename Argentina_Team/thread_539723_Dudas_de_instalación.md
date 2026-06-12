---
title: "Dudas de instalación"
date: 2007-08-31
forum: Argentina Team
---

### Post by kha0s101 on 2007-08-31
[COLOR="Green"]Hola, como verán soy nuevo y pido disculpas desde ya por si acaso estoy duplicando posts (usé el buscador y no encontré algo sobre estos temas) . 

Ayer instalé Ubuntu en mi pc y creo que es mejor que XP es solo cuestión de acostumbrarse a su manejo. Pero me surgieron ciertos problemas, de instalación, que espero puedan ayudarme a solucionar:

1. Como instalo un programa desde los paquetes? Por ejemplo, tengo los paquetes de LiVES-0.9.8.6 y kdenlive-0.5-1 para instalar pero no sé como hacerlo, no puedo hacer que synaptic me busque los archivos en mi pc.

2. Instalé Opera 9.23 pero no trae el archivo de lenguaje en español, así que lo descargué pero no puedo completar el proceso porque no tengo permiso de copiado a usr/share/opera/locale y si intento cambiar de usuario, para loguearme como root, GNOME no me lo permite ya que instalé Kubuntu.

3. Como puedo desinstalar Kubuntu por completo? quiero quedarme solo con GNOME.

4. Que pasos debo seguir para poder *ver* una pc con Windows en red? Aclaración: son solo 2 pcs en la red conectadas mediante cable de red (sin hubs o nada parecido)

Saludos.[/COLOR]

---

### Post by spg76 on 2007-08-31
1. ¿Qué tipo de páquetes tenes? Si son .deb simplemente haciendo doble clic los instalas (salvo que tengan alguna dependencia rara). Si son tar.gz tenes que compilarlos manualmente lo que es un poco más complicado.
Hay paquetes . deb de LiVES en [http://www.getdeb.net/app.php?name=LiVES](http://www.getdeb.net/app.php?name=LiVES)
De kdenlive no sé donde hay.

2. Tipea en una terminal:

```
gksu nautilus
```

Te pedirá la contraseña y te va abrir Nautilus como root y podes copiar el archivo donde lo necesites. 

3. No sé. Seguro alguien te da una mano en los próximos posts.

4. Idem anterior.

---

### Post by leo_rockway on 2007-08-31
hola, bienvenido al foro y bienvenido a ubuntu.

voy a hacer lo posible por contestar tus preguntas.

para copiar el archivo del idioma espaniol de opera hace lo siguiente desde consola:

```
sudo cp [archivo] /usr/share/opera/locale
```

donde [archivo] es la direccion del archivo que queres copiar (por ej: /home/usuario/ouw923_es-ES.lng)

ubuntu no viene con usuario root per se. lo que se usa es sudo que te deja actuar como si fueses root sin serlo (el usuario que viene creado por defecto tiene capacidad sudo). esto es por una cuestion de seguridad (no como en xp que el usuario por defecto es root y en cualquier momento rompe todo). no es recomendable usar sudo sin necesidad; es decir que no es conveniente que ejecutes gnome como root. solamente usalo para aquellos programas que creas necesario. podes usarlo para correr nautilus, por ejemplo, de creerlo conveniente, pero siendo conciente de los cambios que estas haciendo y dejar de usarlo como root cuando ya no es necesario.

para desinstalar kde si no me equivoco tenes que hacer lo siguiente

```
sudo apt-get remove kubuntu-desktop
```

para armar una red con windows necesitas instalar samba. tiene que estar en synaptic (a mi me figura en adept, asi que en synaptic tiene q estar)

los programas esos q tenes (LiVES-0.9.8.6 y kdenlive-0.5-1) son paquetes .deb? si es asi tenes q hacer lo siguiente:

```
sudo dpkg -i nombredelpaquete.deb
```

yo tuve problemas con el kdenlive... una fea pesadilla de dependencias, pero quizas sea xq no estoy usando feisty. contame si logras instalarlo.

salu2

---

### Post by kha0s101 on 2007-08-31
[COLOR="Green"]Gracias a todos por responder :)

Por lo demás, que nivel el de las respuestas y que rapidez!! :):)

Voy a ponerme este finde con eso y a contarles mi experiencia, con suerte será útil para alguien mas.[/COLOR]

---

### Post by kha0s101 on 2007-09-01
[COLOR="Green"]Hola gente.

Esta mañana, me deshice de las obligaciones para seguir con Ubuntu pero hay algo que me ha tenido las ultimas 5 horas sin poder solucionar.

Al encender la pc, Kubuntu (c/Gnome) arranca con resolución 640x480 a 85 mhz (casi inusable), cuando estaba configurada (y funcionando sin problemas) a 1024x768 a 75 mhz :confused:

Tengo una placa onboard ati radeon xpress 200 en un mother intel d101. Lspci la detecta como:

- **ATI Technologies Inc Radeon Xpress 200 Host Bridge (rev 01)**

- **VGA compatible controller: ATI Technologies Inc RC410 [Radeon Xpress 200]**

Googleando encontré algunas soluciones pero no me resultaron. 

Ejemplos: 

- Si habilito el controlador desde el Gestor de Controladores Restringidos, no se inicia Kubuntu en modo normal porque se bloquea y queda el monitor en negro, debo iniciar en Recovery.

- Probé a instalar Automatix. Instalé NDISWrapper para ver si servía de algo pero nada. No hay drivers para ATI aunque sí para Nvidia (que eNvidia jeje... chiste viejo :( ). Tampoco encontré nada útil en Miscellaneous o en Utilities.

Finalmente, a punto de rendirme y escribir un post para molestarlos nuevamente, me encontré con que en un foro en inglés, alguien tenía exactamente el mismo problema que yo. En [**éste thread**]("http://www.linuxforums.org/forum/ubuntu-help/64489-ati-radeon-xpress-200-cant-change-screen-resolution.html")

Allí, finalmente se comenta la solución que consiste en:
```

sudo apt-get update
sudo apt-get install linux-restricted-modules-$(uname -r) #Okay if it is already installed
sudo apt-get install xorg-driver-fglrx
sudo depmod -a
sudo aticonfig --initial
sudo aticonfig --overlay-type=Xv

y reiniciar el equipo.
```

Lo cual, para un inexperto en Linux como yo suena más difícil de entender que Klingon o el código de Matrix :lolflag:

Espero que algún gurú del foro pueda comentarlo para nuestra iluminación. 

**Nota**: alguna manera que puedan sugerir para estudiar los comandos de Linux? Vi que el comando man tiene todo pero tiene alguna organización, del estilo: "comandos para configurar la red" o algo  así?

Hay una segunda parte de comandos  de consola para verificar que todo está en orden pero ya al presentar la pantalla de logueo, puedes ver que ha vuelto a su antiguo 1280x1024 a 60 mhz, y que luego se puede configurar sin problemas.

El problema no es nuevo pero en ése thread está la solución que hasta ahora ha funcionado bien (reinicié el equipo para probar que aún seguía funcionando el cambio de resoluciones)

Espero que le sea útil a alguien. Me voy a almorzar y ya toca partido de fútbol esta tarde así que supongo que desde el lunes comenzaré a probar el tema de la Edición de Video semiprofesional. Es todo lo que me queda para dejar de una vez Micro$oft :guitar:

Slds.[/COLOR]

---

### Post by kha0s101 on 2007-09-04
[COLOR="Green"]Hola gente. Gracias por sus consejos.

Pude desinstalar kubuntu con la única novedad que luego no tenía teclado!! pero reinicié en Recovery Mode para luego entrar normalmente.

Instalé y probé Kdenlive (necesita **mlt++_cvs20070101_i386** y **mlt_cvs20070101_i386** para funcionar), Kino, LiVES pero en ningún caso conseguí que funcionen con un archivo pequeño, de 1 gb (sobre todo cuando una captura de buena calidad toma mas o menos unos 13 gb/h. Visto así, esta parte seguiré trabajándola en la windola, lo cual aunque no me gusta era inevitable porque tengo una placa Pinnacle y creo que es imposible capturar sino es con el programa de la misma empresa, que corre solo en Window$.

Pude cambiarle el idioma a Opera y de las opciones que ví (FF, IE, Konqueror, Opera), es el más fiel al diseño de la web, en especial el tema de las fonts que muestra, pero es muy lento, así que aguante Firefox:guitar:

**Otras Incógni**tas :lolflag:

Si alguien del foro tiene por casualidad un teclado Genius Comfy KB-21e-Scroll con todas sus teclas configuradas, podría indicarme como hacer :confused:

Probé varias alternativas: usé xbindkeys para lograr que el botón **Media** ejecute Amarok pero no logro que me tomé los botones "office" ni asignar algo a **My Computer**. Por otra parte, eché mano a **Combinaciones de Teclas** de Ubuntu para hacer funcionar las correspondientes a play/pause, etc

Vi tutoriales donde trabajan con *xbindkeys -k* pero la captura de las teclas no funciona con las teclas "office" y en general con casi ninguna de las teclas especiales.

También use Keytouch pero no tuvo efecto alguno.

Última: alguien sabe como hacer para cambiar el reproductor de mp3 predeterminado? Yo quiero poner Amarok (o quizás Listen) y actualmente me sale Rhythmbox.

Saludos[/COLOR]

---

### Post by faktorqm on 2007-09-05
hola, no puedo contestar a nada de lo que respondiste, salvo a las asociaciones de archivo. agarras el formato de audio que quieras asociar, por ejemplo, prueba.mp3, haces click derecho, propiedades. Vas a la ficha "abrir con..." y ahi seleccionas la aplicacion para todos los mp3. espero que te sirva. salu2!

---

### Post by kha0s101 on 2007-09-06
[COLOR="Green"]Gracias amigo por responder. Lamentablemente, no funcionó... no hay forma de sacar a Rhythmbox... pero en fin, tampoco es nada grave :popcorn:

Saludos.[/COLOR]

---

### Post by faktorqm on 2007-09-07
bueno, sino tenés la opción de desinstalar el ryhtmbox, o como se escriba xD, si es que verdaderamente no te gusta. salu2!!

---

### Post by kha0s101 on 2007-09-08
[COLOR="Green"]Ja ja!! ni para tanto!!! era solo para aprender como se hacía. Pero por lo demás, estoy muy satisfecho con Rhythmbox y con Ubuntu en general.

Saludos.
[/COLOR]

---

