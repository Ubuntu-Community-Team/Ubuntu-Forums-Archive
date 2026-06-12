---
title: "[SOLVED] Arrancar Nautilus"
date: 2007-09-09
forum: Argentina Team
---

### Post by Vero1 on 2007-09-09
Hola,

Soy bastante nueva con Ubuntu Feisty, así que necesito que por favor me digan cómo hacer correr Nautllus.

Cuando aparece el Escritorio, tambien aparece por unos segundos Nautilus, con una leyendita en la parte inferior que dice Panel, pero no me dá oportunidad de hacer nada.

Descargué todo lo que pertenece a Nautilus desde Synaptic.

Gracias por adelantado y saludos:)

---

### Post by spg76 on 2007-09-09
Podés hacer Alt+F2 y escribir "nautilus".
O, lo que es más sencillo, iniciarlo desde el menú "Lugares>Carpeta Personal".
Saludos.

---

### Post by Vero1 on 2007-09-09
Hola,

Gracias por contestar.

Cuando aprieto Alt+F2 me contesta que no encuentra el Archivo.

Cuando voy a Lugares-Carpeta Personal, no figura...

Qué puedo hacer?

Gracias de nuevo.

---

### Post by undiaperfecto on 2007-09-09
probaste con "sudo nautilus" desde el terminal?

---

### Post by clasificado on 2007-09-10
A mi se me hace que se te *****
proba reinstalarlo desde el synaptic o corriendo desde la consola

sudo apt-get remove nautilus && sudo apt-get install nautilus

Clasificado

---

### Post by Vero1 on 2007-09-10
> **undiaperfecto said:**
> probaste con "sudo nautilus" desde el terminal?

Gracias por responder.


Sí, justamente ayer probé y sale la ventana de Nautilus, pero me pregunto por qué no se puede manejar cuando sale la pantallita al comienzo de Ubuntu?

saludos

---

### Post by Vero1 on 2007-09-10
> **clasificado said:**
> A mi se me hace que se te *****
proba reinstalarlo desde el synaptic o corriendo desde la consola

sudo apt-get remove nautilus && sudo apt-get install nautilus

Clasificado

Gracias probaré.

saludos

---

### Post by Vero1 on 2007-09-10
Bueno probé lo que me dijiste y desde la terminal me sale la siguiente pantalla:

[[IMG]http://img127.imageshack.us/img127/2084/pantallamw1.th.png[/IMG]](http://img127.imageshack.us/my.php?image=pantallamw1.png)


Qué hay que hacer?

gracias

---

### Post by nest on 2007-09-10
anda a System>Administration>Synaptic...

cuando habras el Synaptic anda a Search y pone **libgnomevfs**

instala el librería y corre conky denuevo.

---

### Post by Vero1 on 2007-09-11
Hola nest,

Gracias por la contestación pero yo tengo problemas con nautilus.
Te referís a éso no y no a conky?

---

### Post by Vero1 on 2007-09-11
> **nest said:**
> anda a System>Administration>Synaptic...

cuando habras el Synaptic anda a Search y pone **libgnomevfs**

instala el librería y corre conky denuevo.

Nest, busqué la librería en Synaptic y está pero cómo se instala?

---

### Post by Vero1 on 2007-09-11
nest, no hagas caso del quote anterior.
Hay unos cuantos pero seguidos de numeros. Algunos ya están instalados. "libgnomevfs" solo no está.

---

### Post by Vero1 on 2007-09-11
Ahora me sale esta info cuando corro nautilus desde la terminal.
Qué es lo que tengo que hacer?

[[IMG]http://img405.imageshack.us/img405/8981/infogp0.th.png[/IMG]](http://img405.imageshack.us/my.php?image=infogp0.png)

---

### Post by ubuntu27 on 2007-09-11
Cual es el prblema que tienes con Nautilus? En uno de tus screenshots veo algo que dice "Root-Nav..."  eso no es nautilus?

---

### Post by jorgito on 2007-09-11
Hola a todos, 

Me parece que lo que dice vero1 es que no podia hacer nada con el splash screen del nautilus. Bueno, al menos para mi es un splash screen, ya que a pesar de tener unos iconitos medio difusos cuando arranca no me deja hacer nada a mi tampoco. Hasta donde entendi, el nautilus es en ubuntu lo que el explorador de archivos en güindous. Que alguien chifle si me equivoco. 
Ahora puede estar pasando que despues de tanto toqueteo el submarino este haciendo agua....

Saludos!

---

### Post by Vero1 on 2007-09-11
> **jorgito said:**
> Hola a todos, 

Me parece que lo que dice vero1 es que no podia hacer nada con el splash screen del nautilus. Bueno, al menos para mi es un splash screen, ya que a pesar de tener unos iconitos medio difusos cuando arranca no me deja hacer nada a mi tampoco. Hasta donde entendi, el nautilus es en ubuntu lo que el explorador de archivos en güindous. Que alguien chifle si me equivoco. 
Ahora puede estar pasando que despues de tanto toqueteo el submarino este haciendo agua....

Saludos!

Jorgito, es como vos decís, no puedo hacer nada porque en unos segundos desaparece. Me parece que no tiene sentido que sea así y por eso creo que algo no está bien configurado o falta algo para instalar...

saludos

---

### Post by Vero1 on 2007-09-11
> **ubuntu27 said:**
> Cual es el prblema que tienes con Nautilus? En uno de tus screenshots veo algo que dice "Root-Nav..."  eso no es nautilus?

ubuntu 27, mi problema es que puedo hacer correr Nautilus desde la terminal pero no puedo hacer nada con la ventana que aparece cuando entro en Ubuntu porque desaparece en unos segundos. No veo lógico que aparezca y luego desaparezca sin que pueda hacer algo.

En mi último screenshot habla de que un share no está habilitado y pregunto qué debo hacer para habilitarlo.

saludos

---

### Post by marianom on 2007-09-11
IMHO, ese splash te muestra que aplicaciones están iniciandose dentro del entorno del escritorio. No hay nada que hacer con eso, solo te muestra un grado de avance (para que la gente no se pregunte "¿por qué tarda tanto?").

---

### Post by Vero1 on 2007-09-11
Gracias marianom, por fin alguien me aclara el presunto problema.

Ahora, si sos tan amable, me podés indicar qué debo hacer con el error que me sale en el último screenshot que envié, donde habla del share que está inhabilitado?

gracias

p.d.

Qué quiere decir IMHO?

---

### Post by jorgito on 2007-09-11
Vero1. 

IMHO viene de In My Humble Opinon (en mi humilde opinion).
En 
[http://www.eps.mcgill.ca/jargon/jargon.html](http://www.eps.mcgill.ca/jargon/jargon.html)
tenes un monton de cosas mas....
BTW, FYI, mi preferida creo que es "Attoparsec"

Saludos!

---

### Post by marianom on 2007-09-11
> **Vero1 said:**
> Ahora, si sos tan amable, me podés indicar qué debo hacer con el error que me sale en el último screenshot que envié, donde habla del share que está inhabilitado?

*Puedo estar errado* porque realmente no es mi área de expertise pero creo que está intentando habilitar el servicio de share (samba y/o nfs) y no lo tenés habilitado/instalado así que no tiene nada que hacer.

Calculo que necesitas el paquete nautilus-share instalado (si vas a Sistema->Administración->Carpetas Compartidas vas a poder tener seguridad).

Salvo que me digas que tenés que compartir una carpeta en red con un windows usando samba yo te diría que no te preocupes por ese error. Lo ves porque ejecutas nautilus desde la línea de comandos (algo que no estoy seguro porque lo haces).

Le pedimos por favor a la amable concurrencia que me corrija si estoy errado.

---

### Post by Vero1 on 2007-09-11
marianom,

En Carpetas Compartidas no hay nada.
En Propiedades Generales: Compartición con Windows:
Dominio/Grupo de trabajo: MSHOME.

En cuanto a por qué corro Nautilus desde la linea de comandos es porque no sé de qué otra manera lo puedo hacer.

gracias

---

### Post by Vero1 on 2007-09-11
Gracias jorgito por la info:)

---

### Post by ubuntu27 on 2007-09-11
Nautilus es un navegador de direcotorios, es como WIndows Explorer, aunque mucho mas que eso.

Lo que aparece al inciar Ubuntu, es un Splash Screen (no se como lo llaman en espanol), lo cual muestra los servicios que estan siendo cargados.

Lo unico que tienes que hacer para abrir nautilus es ir a Places (Lugar) y escoger donde como Home, CD, Computer, etc.

Aqui una pequenya guia en ["Como puedo agregar iconos (Home, Papelera, etc ) en el escritorio]("http://www.ubuntu-es.org/index.php?q=node/54066")

[http://www.ubuntu-es.org/index.php?q=node/54066](http://www.ubuntu-es.org/index.php?q=node/54066)

[http://kernelsource.org/2007/04/06/mostrar-iconos-de-sistema-en-gnome/](http://kernelsource.org/2007/04/06/mostrar-iconos-de-sistema-en-gnome/)

---

### Post by Vero1 on 2007-09-12
Hola Ubuntu27,

Probé lo que me indicas pero sigue sin aparecer nautilus en el escritorio...

saludos

---

### Post by ubuntu27 on 2007-09-12
> **Vero1 said:**
> Hola Ubuntu27,

Probé lo que me indicas pero sigue sin aparecer nautilus en el escritorio...

saludos

> **Vero1 said:**
> Ahora me sale esta info cuando corro nautilus desde la terminal.
Qué es lo que tengo que hacer?

[[IMG]http://img405.imageshack.us/img405/8981/infogp0.th.png[/IMG]](http://img405.imageshack.us/my.php?image=infogp0.png)

Si te sale nautilus, alli veo en tu screenshot. Lo que dice Root - Navegador de [Archivos], eso es nautilus. 

NAUTILUS (Navegador de Archivos):
[[IMG]http://img529.imageshack.us/img529/1853/trootfilebrowserik7.th.png[/IMG]](http://img529.imageshack.us/my.php?image=trootfilebrowserik7.png)

Vuelve a abir nautilus (Navegador de Archivos), click en AYUDA, y luego ACERCA DE...

Alli veras que dice Nautilus y su version.

[[IMG]http://img514.imageshack.us/img514/9595/aboutnautilusaj0.th.png[/IMG]](http://img514.imageshack.us/my.php?image=aboutnautilusaj0.png)

---

### Post by Vero1 on 2007-09-12
Sí Ubuntu27, lo tengo a Nautilus pero al no estar el ícono en el escritorio(que no sé cómo ponerlo) lo tengo que correr desde Terminal.
La verdad es que a pesar de todo lo que me indican, no tengo forma de "llamarlo" si no es con Terminal.

---

### Post by spg76 on 2007-09-12
Vero1, para habilitar Nautilus en el menú "Aplicaciones", hace clic derecho sobre el y anda a "Editar los menús".
Fijate en el menú "Accessorios" y busca "Navegador de archivos", habilitalo y ahora te aparecerá en el menú.
Espero que te sirva.

---

### Post by Vero1 on 2007-09-12
Hola spg76,

Gracias por querer ayudarme pero esto se está complicando.

No figura Navegador de Archivos...

Me estoy volviendo loca ya.

saludos

---

### Post by Mafber on 2007-09-12
Vero1, no te desesperes :)
mirá este link es algo que [Como-poner-iconos-del-sistema-en-el-escritorio-de-gnome]("http://www.markdbd.com/2007/03/05/%c2%bfcomo-poner-iconos-del-sistema-en-el-escritorio-de-gnome/")
Suerte!!!

---

### Post by Vero1 on 2007-09-12
> **Mafber said:**
> Vero1, no te desesperes :)
mirá este link es algo que [Como-poner-iconos-del-sistema-en-el-escritorio-de-gnome]("http://www.markdbd.com/2007/03/05/%c2%bfcomo-poner-iconos-del-sistema-en-el-escritorio-de-gnome/")
Suerte!!!

Gracias otra vez Mafber. Lo veré:)

---

### Post by Vero1 on 2007-09-12
> **Vero1 said:**
> Gracias otra vez Mafber. Lo veré:)

Estamos como antes. Lamentablemente no encontré el modo de poner un ícono de Nautilus en el escritorio:(

Vos lo tenés?

---

### Post by Mafber on 2007-09-12
Pregunta: que es lo que querés hacer con el nautilus? explorar tus carpetas (Mis Documentos o Mi Pc)? acordate que en ubuntu el "nautilus" es, lo que en windows, se llama  "explorador de windows" (o Mi Pc del escritorio de windows)

---

### Post by Mafber on 2007-09-12
si queres que nautilus se habra en tu carpeta personal (Mis Documentos) 

"ejecutaremos ya sea desde la terminal como pulsando ALT + F2 introduciendo gconf-editor.

Una vez ejecutado, buscamos la siguiente configuración: apps -> nautilus -> desktop, desde la cual podemos escoger entre los siguientes iconos para poner en el escritorio:

    * Computer icon => Equivale a mi pc en windows
    * Documents icon => Mis documentos
...."
Tenés que activar los que querés usar. Cuando los actives vas a poder ver el icono en el escritorio.

COPIADO (extraído) de [www.markdbd.com]("http://www.markdbd.com/2007/03/05/%c2%bfcomo-poner-iconos-del-sistema-en-el-escritorio-de-gnome/")

Un último concejo... mirá esta [pagina]("http://tuxpepino.wordpress.com/2007/05/17/tip-crear-lanzador-acceso-directo/") que te enseña como hacer un acceso directo (lanzador) y fijate en el ejemplo que da. Creo que te puede servir.

Te muestro mi escritorio dende se pueden ver el lanzador del nautilus ("explorador de linux" cuak)  y la papelera
[escritorio]("http://img400.imageshack.us/my.php?image=pantallazoxh2.png")
Suerte!!!!! :)

---

### Post by Vero1 on 2007-09-13
Hola Mabfer,

Hice todo lo indicado pero lo único que me aparece en el escritorio es la papelera y equipo. En equipo tampoco aparece Nautilus.
Esto es desesperante ya.

El fondo de tu escritorio, precioso!

Decime, qué más puedo hacer??????

Ví los links pero no veo nada claro con respecto al lanzador...

gracias por tu paciencia.

---

### Post by Vero1 on 2007-09-13
> **Mafber said:**
> Pregunta: que es lo que querés hacer con el nautilus? explorar tus carpetas (Mis Documentos o Mi Pc)? acordate que en ubuntu el "nautilus" es, lo que en windows, se llama  "explorador de windows" (o Mi Pc del escritorio de windows)

Lo único que quiero es un lanzador de Nautilus en el escritorio. Hay que elegir o Mis Documentos o Mi PC? Bueno, prefiero Mis Documentos entonces.

Hay algo que no me queda claro. O es Nautilus o es Gnome?

---

### Post by Mafber on 2007-09-13
Hola Vero1!!! No es necesario elegir uno u otro ícono. Podes tener los dos o todos los que vos quieras. Eso es a gusto personal :)
Gnome es (ojo que es mi interpretación... :( ya que a mi tampoco me queda claro qué es) es el escritorio, algo así como "el programa que establece como hacer las cosas, en particular lo que tiene que ver con lo grafico". Hay otros escritorios que son KDE y Xfce que viene en Kubuntu y en Xubuntu.
Nautilus es el "Explorer" en windows

Gnome = Ubuntu
KDE = Kubuntu
XfCE = Xubuntu

---

### Post by Vero1 on 2007-09-13
Mabfer,

Hice unas pruebas con el Editor de Configuraciones. Tildé y destildé
para que se vea o no Mis Documentos, pero no aparece.
En cambio si destildo y tildo Computer entonces sí aparece o desaparece el ícono.

Hay una leyenda que habla sobre si está como "true" entonces aparece el ícono. Evidentemente Mis Documentos no debe estar como "true" y éso ya pertenece a programación o a alguna configuración, creo.

---

### Post by Mafber on 2007-09-13
Te paso el una captura de como lo tengo configurado.
Espero que te sirva
[captura]("http://img212.imageshack.us/my.php?image=pantallazo1yr4.png")

---

### Post by Vero1 on 2007-09-13
[[IMG]http://img110.imageshack.us/img110/3610/configyo1.th.png[/IMG]](http://img110.imageshack.us/my.php?image=configyo1.png)

---

### Post by Vero1 on 2007-09-13
> **Vero1 said:**
> [[IMG]http://img110.imageshack.us/img110/3610/configyo1.th.png[/IMG]](http://img110.imageshack.us/my.php?image=configyo1.png)

Salió mal, salió el lanzador tambien:(

Bueno, hay una diferencia con el tuyo. En Desktop icon yo no tengo un valor y seguramente por eso no sale...

---

### Post by Mafber on 2007-09-13
Bien, veo que lo pudiste poner... Tenes Mis Documentos (carpeta personal de veronica) 
El que no veo es el de computer icon (mi pc) pero es lo mismo que el de mis documentos pero en vez de que se te habra el nautilus en tu carpeta personal, se habre en el directorio raiz :popcorn:

---

### Post by Vero1 on 2007-09-14
Hola Mabfer,

Cuál sería el Directorio Raíz? Porque abra la carpeta que abra, Nautilus brilla por su ausencia:(

saludos

---

### Post by Mafber on 2007-09-14
Hola Vero!!! decime: a que le llamas nautilus? En windows vos no ves el "explorer", ves el explorador de windows o el internet explorer. aca en ubuntu cuando ejeculas el nautilus lo que ves es el programa que te deja ver los archivos en tu disco rígido (el icono de "carpeta personal de verinica").
Directorio raiz: es lo que vos en windows llamás "C:" donde estan todas la carpetas.

---

### Post by vk-cdg on 2007-09-14
Pregunta ¿si vas al menú Lugares y luego elegís "Carpeta Personal" o en su defecto "Equipo" se abre una ventana? ¿en esa ventana ves cierto contenido de acuerdo a cual abriste?

Bueno, esa ventana es el Nautilus. El Nautilus en en Ubuntu lo mismo que el Explorador de Windows en Windows.

Si no me expliqué avisame please.

---

### Post by Vero1 on 2007-09-14
> **Mafber said:**
> Hola Vero!!! decime: a que le llamas nautilus? En windows vos no ves el "explorer", ves el explorador de windows o el internet explorer. aca en ubuntu cuando ejeculas el nautilus lo que ves es el programa que te deja ver los archivos en tu disco rígido (el icono de "carpeta personal de verinica").
Directorio raiz: es lo que vos en windows llamás "C:" donde estan todas la carpetas.

Hola Mafber,
Volvemos a lo de antes. Si abro carpeta personal o cualquier otra Nautilus no aparece para nada y tampoco tengo un ícono en el escritorio para lanzar la aplicación.
Éso es lo que me interesa tener. Un ícono de Nautilus en el escritorio por si quiero usarlo en lugar de Gnome.
Me explico?

---

### Post by Vero1 on 2007-09-14
> **vk-cdg said:**
> Pregunta ¿si vas al menú Lugares y luego elegís "Carpeta Personal" o en su defecto "Equipo" se abre una ventana? ¿en esa ventana ves cierto contenido de acuerdo a cual abriste?

Bueno, esa ventana es el Nautilus. El Nautilus en en Ubuntu lo mismo que el Explorador de Windows en Windows.

Si no me expliqué avisame please.

Hola,
Si voy a Lugares y abro Carpeta Personal se abre una ventana donde figura el Escritorio, Examples, Papelera y unas cuantas cosas mas.

Pero por ejemplo en Windows yo tengo un ícono en el Escritorio que corresponde al Explorador de Windows y éso quisiera tener tambien en Gnome pero de Nautilus. Me explico?

gracias

---

### Post by Vero1 on 2007-09-14
Siguiendo con Nautilus, al correrlo desde Terminal, se me abre pero me sale, al último, una leyenda que no sé qué hacer con ella.
Aquí va el screenshot.
Si sabes algo al respecto, te lo agradezco desde ya.

[[IMG]http://img502.imageshack.us/img502/9511/pantallazoveronicaveradme7.th.png[/IMG]](http://img502.imageshack.us/my.php?image=pantallazoveronicaveradme7.png)

---

### Post by jorgito on 2007-09-14
Vero1, 

Al abrir la carpeta personal, o cualquier otra, o cada vez que mires un directorio, o la red o lo que sea, lo que tenes es justamente al nautilus en pleno funcionamiento!!
No necesitas un icono ni nada. Abrir "lugares" cualquiera que este sea, es disparar el nautilus.
No me parece correcto lo de querer usar el nautilus en lugar de gnome, simplemente porque son cosas diferentes. El nautilus viene a ser el explorador de archivos que usa el gnome, por lo tanto estan a niveles diferentes.
Si te sentis intranquila por no tener un icono que arranque el nautilus, o pensas que te estas perdiendo de algo por no ver como se arranca, pensa que es como si en guindous no tuvieras el icono de "mis documentos" en el escritorio. Siempre podes llegar a "mis documentos" desde el explorador de archivos.

Espero que te sea util

saludos!

---

### Post by vk-cdg on 2007-09-14
No termino de entender para que necesitás un ícono de Nautilus, pero lo que podés hacer, es mediante el método que te dieron antes, es poner un ícono de "Equipo" en el escritorio. Eso es como abrir Mi PC en Windows que es mas o menos equivalente a abrir un explorador de windows sin la barra de carpetas.

Digamos, acá no se puede poner un lanzador de Nautilus, los lanzadores son justamente cualquiera de los items que están en el menu lugares.

Linux es linux, no tratemos de hacelo parecer a windows, sino de acostumbrarnos nosotros a el. Por algo elegimos software libre no? porque es algo distinto!

---

### Post by Vero1 on 2007-09-14
Hola amante de "guindous":)

Muy clara la explicación que agradezco.
Bueno, creo que no necesito seguir con este tema.
Ahora, lo único que me queda es saber qué significa lo que sale en Terminal, al final del screenshot, para dar o no por terminado el tema.

A vos, muchas gracias.

---

### Post by Hei Ku on 2007-09-14
cuando abras un programa de escritorio a traves de la terminal vas a ver un monton de mensajes informativos que, normalmente, no representan ningun programa.
En general, son mensajes informativos que dan informacion sobre como esta corriendo el programa, pero no tienen la importancia suficiente para mostrarlo por pantalla.

De hecho, una tecnica comun para encontrar un problema en algun programa grafico es correrlo desde una terminal y ver que mensajes aparecen. Vas a ver que es un consejo muy comun.

Resumiendo, si al correr normalmente no te da un error, no te preocupes, los mensajes que da en la terminal son probablemente inocuos.

---

### Post by Vero1 on 2007-09-15
Gracias una vez mas Hei Ku. Lo doy por terminado.:)

saludos

---

