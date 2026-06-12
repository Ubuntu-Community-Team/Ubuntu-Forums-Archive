---
title: "Geubuntu 7.10 - Luna Nuova - i386"
date: 2008-03-08
forum: Argentina Team
---

### Post by andy_91 on 2008-03-08
alguien sabe donde lo puedo conseguir?


es que de la web oficial ya no se puede bajar


Geubuntu 7.10 - Luna Nuova - i386


Moonlight Edition

desde ya gracias

---

### Post by gmunioz on 2008-03-08
Hola and...:
Lo que ocurre es que por problemas con Canonical, debido a que tiene repositorios propios ahora cambió su nombre a Opengeu, su sitio de descarga es:
[http://linux.softpedia.com/get/System/Operating-Systems/Linux-Distributions/OpenGEU-30565.shtml](http://linux.softpedia.com/get/System/Operating-Systems/Linux-Distributions/OpenGEU-30565.shtml)
Saludos.

---

### Post by andy_91 on 2008-03-08
gracias ya la estoy bajando ;)

voy a ver que onda con esta

---

### Post by andy_91 on 2008-03-09
[[IMG]http://img80.imageshack.us/img80/1747/pantallazofd0.th.jpg[/IMG]](http://img80.imageshack.us/my.php?image=pantallazofd0.jpg)

ya esta instalado en mi pc parese funcionar muy bien pero es dificil a comparacion de gnome, xfce o kde

---

### Post by andy_91 on 2008-03-14
> **andy_91 said:**
> [[IMG]http://img80.imageshack.us/img80/1747/pantallazofd0.th.jpg[/IMG]](http://img80.imageshack.us/my.php?image=pantallazofd0.jpg)

ya esta instalado en mi pc parese funcionar muy bien pero es dificil a comparacion de gnome, xfce o kde
alguien sabe como personalizo el panel superior

es que de tanto en tanto me desaparese la hora y quiero agregar el volumen y el clima

---

### Post by gmunioz on 2008-03-15
Hola and..:
Te dejo una guia de E17, puede que te oriente:

Enlightenment es un escritorio ligero, no tiene escritorio, por lo tanto no tiene iconos en la pantalla ni nada, aunque podemos ponérselos.

Pues bien dejando claro que enlightenment es un entorno altamente configurable, debes entender que por muy dock, o lo que sea, todos los programas son ventanas, y enlightenment tiene unas propiedades para ellas, en que situación se encuentran, si debe ser ignorado por la lista de ventanas, si esta "pegado" al escritorio, que tipo de bordes tiene, etc. Todas estas propiedades las puedes cambiar temporalmente, o bien decir que las recuerde. Puedes acceder a estas opciones apretando con el botón derecho sobre la barra de una ventana:

En algunas ventanas como podrían ser gKrellm, xmms, etc. En las cuales no disponemos de una barra, bastara con apretar alt + botón derecho del ratón. Tenemos que notar que el alt, hace que enlightenment no envíe nada a la ventana y la trate a su manera, así que si un objeto/ventana no se deja mover, podemos apretar alt + botón izquierdo del ratón y moverla donde queramos.

También tenemos que saber, que enlightenment se compone (a grandes rasgos), de tres menús, a los cuales accedes con el botón derecho, central (o izquierdo + derecho) e izquierdo, todos sobre el escritorio:


El User Menus: Es el menú de usuario, el cual es el que usaremos y configuraremos nosotros a nuestro gusto.

El menú "Enlightenment": Es un menú estándar, de aquí cabe destacar los sub-menús de themes, y maintenance, que mas adelante usaremos.

El menú "Settings": Desde aquí configuraremos algunos (no todos) aspectos de enlightenment.

También es muy cómodo saber, que al apretar con el botón izquierdo sobre el botón de maximizar, esta ventana se maximiza, pero, si lo hacemos con el botón central, se expenderá solo en horizontal, y con el botón derecho lo hará en vertical.

Otra cosa que puede hacer enlightenment es poner casi cualquier ventana en pantalla completa, el te ajusta automáticamente una resolución adecuada, es posible que si la ventana es muy pequeña veamos los pixelazos, pero con ventanas medianas grandes puede ser muy cómodo. Al estar en pantalla completa enlightenment ignora los cambios de escritorios virtuales con el ratón.

Por ultimo, es importante saber que toda la configuración se guarda en: ~/.enlightenment/ y en el caso de los dr17components en: ~/.e/

e16menuedit

Esta aplicación nos facilita la tarea de configuración de menús. Al ejecutar e16menuedit nos debería salir algo parecido a esto:

El programa no tiene complicación alguna si quieres agregar un programa seleccionas el sub-menú donde deseas introducirlo, y aprietas "Insert Menu Entry" Description sera el texto que veremos en el menú, icon (no recomendado) es el icono que veremos a su lado y executes es su comando, para eliminar "Delete Menu Entry", apretamos save, y salimos apretando quit, este programa nos puede ahorrar tiempo, pero si quieres crearte un menú algo mas trabajado, tendrás que hacerlo a mano, como se explicara mas adelante, una vez creado a mano, puedes perfectamente ayudarte en su modificación con esta utilidad.

e16keyedit

Esta aplicación nos facilitará configurar nuestros atajos de teclado. 

Tiene varias combinaciones de teclas ya configuradas, con este programa podemos hacer que una combinación de teclas nos haga cualquier cosa, desde ejecutar un comando/programa, a controlar cualquier aspecto de enlightenment. En la lista de Action Used, ya vienen varias "sugerencias". Vamos a enumerar las cosas que a priori nos pueden ser mas útiles, ejecutar un comando/programa: ya que nos permite hacer cualquier cosa, "Move to Desktop 0 1...", esto nos moverá en los escritorios virtuales, raise windows: "enrollar" una ventana, minimizar ventanas, etc. Yo aconsejo poner la tecla de al lado de las "flechas" junto con las "flechas" para cambiar de escritorio virtual. Por defecto el cambio de escritorios virtuales esta configurado en alt+shift+teclas de dirección. Con la acción run command, y eesh, podemos controlar cualquier función de enlightenment que no este en la lista.

A las opciones del menú settings del escritorio, accedemos apretando con el botón derecho en algún área vacía, del escritorio.

Focus Settings

Apretaremos con el botón derecho sobre el escritorio, y accederemos a "Focus Settings", por defecto el foco de las ventanas sigue al puntero, es decir, la ventana activa es la que se encuentra debajo del puntero, esto no suele gustar a muchas personas, seleccionamos "Focus follows mouse clicks" para cambiar esto.

Seleccionaremos también "Clicking in a window always raises it", de este modo si clickamos en una ventana que esta debajo de otra, esta pasara a primer plano.

Otro opción interesante, para seleccionar, puede ser "All new windows first get the focus", de este modo las ventanas recién abiertas serán las activas por defecto, que es lo que normalmente se quiere.

"Raise windows on focus switch" también es recomendado seleccionarlo, si no lo esta ya, de este modo si hacemos alt + tan (por ejemplo), a medida que pasemos las ventanas, estas pasaran a primer plano.

Las opciones de focus lista las dejaremos así, ya que mas adelante veremos como sacar cualquier objeto de esta lista.

Una opción que podríamos probar es "Send mouse pointer to window after focus switch", esto te puede dar agilidad al trabajar, o confundirte mas. Lo que hace es que al cambiar a otra ventana activa, el puntero se posiciona automáticamente en el centro de esta. 

Move & Resize Settings

Cuando movemos y cambiamos el tamaño de una ventana, tiene varias propiedades, las cuales podemos ajustar con este menú.

"Move Methods": Hace referencia al aspecto de la ventana, al ser movida.

"Resize Methods" como veras la ventana cuando la estés redimensionando.

"Move/Resize Geometry Info Position": Puedes hacer que aparezca una ventana con la posición y tamaño actual de una ventana que estas moviendo y/o redimensionando. "Window Center", dicha ventana aparecerá en el centro de la ventana movida y/o redimensionada, "Always Screen corner", los datos de posición - tamaño los veras en la esquina superior izquierda de la pantalla, "Don't show" desactiva esta opción.

Pager Settings

Cuando hablamos del pager hacemos referencia a la/s barra/s, que hay (por defecto), en la esquina inferior izquierda, y nos muestran los escritorios y escritorios virtuales, junto con una miniatura de sus ventanas:

"Enable pager display": nos muestra (o no), el pager.

"Make miniature snapshots of the screen": De este modo veremos las ventanas que tenemos abiertas en miniatura.

"Smooth high quality snapshots in snapshot mode": Realizará (o no), capturas de alta calidad si no le seleccionamos.

"Pop up window title when mouse is over the window": De este modo al tener el cursor encima de una ventana, visualizaremos su nombre.

"Continuously scan screen to update pager": Las screenshots se actualizaran automáticamente cada cierto tiempo.

"Pager scanning speed: xxx lines per second": Si tienes un PC medianamente bueno P3 o superior, recomiendo tenerlo al máximo, esta es la velocidad de capturar las screenshots.

"Mouse button to select and drag windows": Seleccionas el botón del mouse que usaras para elegir las ventanas del pager y moverlas y/o seleccionarlas.

"Mouse button to select desktops": Con este botón te podrás mover a los otros escritorios, sin seleccionar ninguna ventana en especial.

"Mouse button to display pager menu": Con este botón veras, el menu del pager, con algunas opciones rápidas, y acceso al menu que estamos configurando ahora mismo.

Window Placement Settings

Este menu nos ofrece varias opciones, de la posición de las ventanas al salir, etc. 

Multiple Desktop Settings

Aquí seleccionamos cuantos escritorios queremos podemos elegir hasta 32, y trabajar con escritorios virtuales.
"Wrap desktops around": si lo marcamos, al llegar al ultimo escritorio, volvemos al primero. Recuerda que por defecto al girar la rueda del ratón en el escritorio, cambias de escritorio, cada escritorio puede tener propiedades distintas como puede ser el background.

Virtual Desktop Settings

Aquí configuraremos los escritorios virtuales dentro de nuestro escritorio, si tenemos un escritorio virtual de 4x4 en un escritorio, es como tener un escritorio cuatro veces mas grande, dividido en el tamaño de nuestra pantalla. Por defecto, si dirigimos el puntero al lateral de la pantalla, pasaremos al siguiente escritorio virtual, y si lo dirigimos abajo pasaremos al escritorio virtual inferior. Esto se puede desactivar desmarcando la casilla "Enable edge flip", con "Wrap virtuals desktops around", volveremos al primer escritorio después del último, y con "Resistance at edge of screen" configuramos la resistencia de cambio de escritorio virtual, al mover el puntero a algún lado de la pantalla.

Tooltip Settings

Los tooltips son aquellos globos que te salen por defecto dándote consejos e información del funcionamiento de enlightenment, son, por lo general, molestos. Si desmarcamos las dos casillas de Tooltip Settings, no nos molestarán mas, si los queremos conservar podemos configurar además el tiempo que tardan en salir desde que el puntero se estabiliza en un punto.

Audio Settings

Activa algunos sonidos, para ello necesitas Esound.

Group Settings

Configura los aspectos que deben compartir los grupos de ventanas, puedes configurar a que grupo pertenece una ventana, en las opciones de dicha ventana. De este modo si tu mueves una ventana se moverán al unisono las del grupo, si enrollas/minimizas una ventana las del grupo también lo harán.

Remember Settings

Cada vez que le decimos a una ventana que recuerde algunas de sus propiedades, esta pasara a este "registro", desde aquí podemos ver que ventanas recuerdan propiedades, cuales recuerdan, y cambiarlas o eliminarlas.

Special FX Settings

Aquí podemos configurar algunos efectos de varios tipos:

"Slide desktops around when changing": esto hace que al cambiar los escritorios veas el efecto que ves, de sobre posición.

"Slide windows in when they appear": Si la activas, al abrirse una ventana nueva, o ejecutarse un programa, esta aparecerá según el efecto de "Slide Method".

"Animated display of menus": de este modo al aparecer los menús harán el efecto de "desenrollarse".

"Animate shading and unshading of windows": si la activamos, al enrollar una ventana nos dará dicho efecto, de subir y quedar recogida, si no esta activada, no habrá ningún tipo de animación.

Desktop Background Settings

Aquí configuraremos principalmente el fondo de pantalla, para agregar una imagen a la lista de fondos, basta con copiarla a ~/.enlightnement/backgrounds ir al menú de Enlightenment -- maintenance -- regenerate menus, y ya estará agregada a la lista. Ahora seleccionaremos la imagen de fondo que deseamos, si apretamos el botón "Move to Front" nos moverá esa imagen al principio de la lista, con "Ducplicate" la duplicará, con "Unlist" la sacara de la lista, y con "Deleta File" eliminara el archivo en si.

Con la imagen miniaturizada y sus cuatro barras al rededor, podemos modificar el tamaño y posición de la imagen, si la imagen coincide con nuestra resolución de pantalla, este paso puede omitirse.

Con la barra de "Theme transparency", regularemos el nivel de transparencias que tiene el tema, solo el tema, no las demás ventanas, es decir veremos transparentes las barras, menus, y poca cosa mas. Se recomienda un nivel entre 80 y 100. Podemos notar que por defecto los menus, nos transparentan el escritorio, y no la ventana que tenemos debajo, eso lo podemos cambiar con "Advanced Settings", en la columna Menus, marcamos Glass, en lugar de Backround. Si hacemos esto, y además tenemos seleccionada la opción en FX settings para que los menus aparezcan animados, podremos notar que la transparencia de los menus sale desplazada, así que si queremos menus animados, tendremos que transparentar el fondo, y si queremos transparentar los programas y todo lo que haya debajo deberemos prescindir de un menu animado.

Editando menús

Los menus están guardados en ~/.enlightenment/

Con la extensión .menu el user menus es el file.menu, e aquí un ejemplo de un file.menu:

"User Menus" "Applications" NULL menu "genmenu.menu" "Epplets" NULL menu "epplets.menu" "Restart" NULL exec "eesh -e 'restart'" "Others" NULL menu "others.menu" "Log Out" NULL exec "/usr/bin/eesh -e 'exit' "

La primera linea define el nombre a mostrar en el despliegue del menu, por defecto "User Menus".

Y a partir de aquí, introducimos los elementos. Primero el nombre que se mostrara en el menu, entre comillas. Con NULL nos aseguramos de que si el ejecutable o el menu, no existe, no nos lo muestre en el menú. menu/exec, define si estamos poniendo un sub-menú, o un comando. Y por ultimo el comando o el sub-menú, entre comillas. Puedes crear los sub-menús que quieras solo basta con crear un archivo.menu, y hacer referencia a el desde algún menú ya configurado. No nos tenemos que olvidar que después de modificar estos archivos, para que los cambios tengan efecto, tenemos que ir a maintenance, regenerate menus.

Temas

Los temas se guardan en ~/.enlightenment/themes por lo tanto si quieres instalarle alguno solo basta con copiarlo en esta carpeta.

Para cambiar el tema, pulsamos con el botón central sobre el escritorio, nos dirigiremos al sub-menú themes y seleccionaremos el que queramos.

Para modificar un tema basta con trastear con la carpeta en la que esta guardada, para cambiar cursores, etc.

Engage

Engage, por defecto, viene sin ninguna aplicación configurada. Toda su configuración se guarda en ~/.e/apps/engage

Debemos notar que engage es una ventana sin bordes, como cualquier otra, así que apretando con alt + botón xxxx del ratón, podemos moverla y cambiar sus propiedades. Sus temas se guardan en ~/.e/apps/engage/themes con la extensión eet. Vamos a imaginar que decidimos instalarnos el tema exquisite, para ello descargaremos su source y su eet, puede que vayan juntas. El source lo descomprimiremos en ~/.e/apps/engage y el eet lo copiaremos a ~/.e/apps/engage/themes, ahora apretaremos con el botón derecho sobre engage y le apretamos a configuration, y apretamos engage, puede que la ventana salga muy grande, no importa, seleccionamos el tema exquisite, apretamos apply, y salimos, si la ventana es demasiado grande la moveremos con alt + click izquierdo. Lo único que ha cambiado ahora es que si ejecutamos una aplicación que este registrada en el tema exquisite, veremos su icono correspondiente, y si no un interrogante verde, además el tema contiene los efectos, y las fuentes, las de exquisite esta bastante bien. 

Que pasa si queremos definir el icono de un programa, pero no lo queremos en la barra, es decir que al usar nosotros ese programa, en la barra no nos salga un interrogante pero no este siempre el icono en la barra. Pues hacemos lo mismo que antes, pero al finalizar, borramos su eet, de la carpeta launcher, de manera que solo quede en mapping, y listo. Un posible problema que te puedes encontrar, es que quieras poner una aplicación con un icono, y no te deje, es decir te ponga otro icono, debido a que el tema que estas usando, p.eg: exquisite, usa otro icono predefinido para esa aplicación. Para cambiar eso debemos ir a las sources del tema, editar si .edc buscar la linea no del programa, si no del icono que te pone, iras mas rápido, puedes ver los iconos y sus nombres en la carpeta images de la source del tema, una vez has encontrado la linea puedes: cambiarle el icono, borrar la linea o bien comentarla. Sales de tu editor, y ejecutas el script build_theme.sh, eso te creara el nuevo eet, que deberás mover a la carpeta themes sustituyendo al antiguo.

Podemos también agregar unas pequeñas aplicaciones, a la barra, programadas en edje, por defecto al descargarlo te descarga dos: expedition.eet (reloj analógico), y digital.eet. Para instalarlos solo tenemos que crear una carpeta llamada sysicons en ~/.e/apps/engage/ y mover ahí los eet.

Además cabe decir que engage tiene un sitio para aplicaciones como aMule, que pueden usar trayicon.

Por ultimo un poco de control del engage, no tiene mucho misterio, si apretamos sobre un icono, se ejecutara el comando que le configuramos, si apretamos con el botón central, sobre un icono con ventanas abiertas, estas se minimizaran, y si dejamos apretado un segundo el botón izquierdo sobre un icono de ventana minimizada, esta se restaurará.

eesh

eesh es una shell, para controlar enlightenment, podemos ejecutar "eesh -e comando", o bien solo eesh, para entrar en modo interactivo, en modo interactivo si ejecutamos help, veremos una lista de comandos, si hacemos "help comando", veremos la ayuda del comando correspondiente. eesh puede ser sumamente útil para hacer pequeños scripts o para hacer hotkeys, etc.

Eterm como parte del escritorio y del fondo

Si somos de aquellas personas que nos gusta hacerlo todo por consola, que nos gusta ejecutarlo todo por consola, etc. Esta sección nos ira muy bien. En esta sección configuraremos un par de Eterms con tal de tener siempre dos consolas abiertas.

Abriremos una Eterm, desde otra terminal si queremos, de este modo:

$ Eterm -O --shade 70% --cursor-color rgb:0/0/0 --scrollbar=0 --buttonbar=off -F fixed

Ahora la seleccionamos con alt + botón derecho, ponemos border style -- borderless. Ponemos skip window list, para que no salga en alt tab ni nada de nada, ponemos stick, para que salga en todos los escritorios virtuales, y por ultimo, se staking below. Pulsamos remember, y lo activamos todo, menos shaded state, y desktop. De este modo también activaremos restart aplicaction on login, para que se ejecute al principio, con alt + click izquierdo movemos la terminal. Ahora no sale en alt + tab, nunca estará encima de otra ventana, esta en todos los escritorios virtuales. Es como un fondo, puede ser muy útil para ejecutar top, para ver los procesos que mas te gastan, monitorizar logs, reproducir música, tener una ssh, no se cualquier cosa, o simplemente una consola siempre abierta. 

Ahora agregaremos otra, esta vez que si que se vea en, alt + tab, esta nos servirá para mediante atajos de teclado acceder rápidamente a una consola, ejecutar algo, y volverla a esconder, ejecutamos una consola igual que antes, con las mismas propiedades, o no. Esta vez si que le ponemos bordes, del tipo pager, y no le apretamos skip window list, por lo demás queda todo igual, esta la pondremos en el lado izquierdo de la pantalla, de manera que quede algo así (cuando esta desplegado):


Con alt + tab podemos seleccionarlo, apretamos ctrl + alt + R para enrollarlo o desenrollarlo. :P
Saludos

---

