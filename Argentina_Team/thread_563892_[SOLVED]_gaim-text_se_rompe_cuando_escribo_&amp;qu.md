---
title: "[SOLVED] gaim-text se rompe cuando escribo &amp;quot;ñ&amp;quot;"
date: 2007-09-30
forum: Argentina Team
---

### Post by santiagoward2000 on 2007-09-30
Hola gente,
A ver si alguien me puede ayudar. Estuve probando gaim-text y me encanta. Pero hoy encontré un problema: cuando toco la tecla "ñ", se cierra y me aparece este error: Segmentation fault (core dumped)
¿Alguna idea?

---

### Post by Mauro22 on 2007-09-30
Proba con otro tipo de letra !

---

### Post by santiagoward2000 on 2007-09-30
> **Mauro22 said:**
> Proba con otro tipo de letra !

¿Bueno, pero como cambio el tipo de letra en gaim-text?

_Tema aparte:_ me encanta tu imagen. ¿Puedo usarla como ícono para moto4lin?

---

### Post by faktorqm on 2007-10-02
trata de usar iso 8859-1 como codificacion de caracteres, o utf8 (creo) en su defecto. ni idea de como se cambia igual, pero capaz tenia una opcion o un archivo cfg. salu2!

---

### Post by leo_rockway on 2007-10-02
por que 8859-1 y no 8859-15?

---

### Post by faktorqm on 2007-10-02
por que en realidad la 15 es la misma que la 1 pero con el simbolo del euro, y un par más que faltaban en la codificacion 1. (la codificacion 15 difiere solo en 8 caracteres de la original 1).
si necesitas escribir el simbolo del euro cuando uses el gaim esa la 15 por que la 1 no lo tiene. salu2!!!!!!

---

### Post by santiagoward2000 on 2007-10-02
> **faktorqm said:**
> trata de usar iso 8859-1 como codificacion de caracteres, o utf8 (creo) en su defecto. ni idea de como se cambia igual, pero capaz tenia una opcion o un archivo cfg. salu2!

Hola gente. Estuve tratando de hacer lo que dijo faktorqm, pero no encuentro ningun archivo que me deje cambiar la cadificacion. ¿Alguien sabe donde esta?
Gracias

---

### Post by nest on 2007-10-02
> **santiagoward2000 said:**
> Hola gente. Estuve tratando de hacer lo que dijo faktorqm, pero no encuentro ningun archivo que me deje cambiar la cadificacion. ¿Alguien sabe donde esta?
Gracias

No es un archivo el que te lo permite realizar. es a través de la configuración de la terminal. según cual uses.

yo uso xterm y te lo permite (en este momento estoy en el trabajo y no puedo pasteartela).

si usás urxvt también lo permite. pone -h y fijate que te lo explica si mal no recuerdo. sino man urxvt o man xterm y listo.

nose si lo solucionará pero lo que buscás se hace desde la configuración de la consola.

---

### Post by santiagoward2000 on 2007-10-02
Buscando en man xterm encontre esto:
>        -en encoding
               This option determines the encoding on which  xterm  runs.   It
               sets  the locale resource.  Encodings other than UTF-8 are sup&#8208;
               ported by using luit.  The -lc option should be used instead of
               -en for systems with locale support.


Pero no se como usarlo. Cuando ingreso -en en la terminal, me da esto:
> santi@santi-laptop:~$ -en
Usage: command-not-found [options] <command-name>

command-not-found: error: no such option: -e
bash: -en: command not found


¿Alguien sabe como se hace?

---

### Post by nest on 2007-10-02
> **santiagoward2000 said:**
> Buscando en man xterm encontre esto:


Pero no se como usarlo. Cuando ingreso -en en la terminal, me da esto:


¿Alguien sabe como se hace?

porque no lo estás haciendo bien. es:

```
xterm -en
```

según lo que dice el man, yo lo tengo diferente. te digo como lo tengo cuando llegue a casa.

---

### Post by santiagoward2000 on 2007-10-02
> **nest said:**
> porque no lo estás haciendo bien. es:

```
xterm -en
```

según lo que dice el man, yo lo tengo diferente. te digo como lo tengo cuando llegue a casa.

Hola nest,
Perdoná mi ignorancia, pero cuando puse xterm -en me dio:
> santi@santi-laptop:~$ xterm -en
xterm:  bad command line option "-en"

usage:  xterm [-/+132] [-C] [-Sccn] [-T string] [-/+ah] [-/+ai] [-/+aw]
    [-b number] [-/+bc] [-bcf milliseconds] [-bcn milliseconds] [-bd color]
    [-/+bdc] [-bg color] [-bw number] [-/+cb] [-cc classrange] [-/+cjk_width]
    [-class string] [-/+cm] [-/+cn] [-cr color] [-/+cu] [-/+dc]
    [-display displayname] [-e command args ...] [-fa pattern] [-fb fontname]
    [-/+fbb] [-/+fbx] [-fd pattern] [-fg color] [-fi fontname] [-fn fontname]
    [-fs size] [-fw fontname] [-fwb fontname] [-fx fontname] [%geom] [#geom]
    [-geometry geom] [-hc color] [-help] [-/+hold] [-iconic] [-/+ie] [-/+im]
    [-into windowId] [-/+j] [-/+k8] [-kt keyboardtype] [-/+l] [-/+lc]
    [-lcc path] [-leftbar] [-lf filename] [-/+ls] [-/+mb] [-mc milliseconds]
    [-/+mesg] [-/+mk_width] [-ms color] [-n string] [-name string] [-nb number]
    [-/+nul] [-/+pc] [-/+pob] [-rightbar] [-/+rv] [-/+rvc] [-/+rw] [-/+s]
    [-/+samename] [-/+sb] [-/+sf] [-/+si] [-/+sk] [-sl number] [-/+sm] [-/+sp]
    [-/+t] [-ti termid] [-title string] [-tm string] [-tn name] [-/+u8]
    [-/+ulc] [-/+ulit] [-/+ut] [-/+vb] [-version] [-/+wc] [-/+wf]
    [-xrm resourcestring] [-ziconbeep percent]

Type xterm -help for a full description.


Después probé xterm -help, y entre todos los comandos que aparecen, vi uno que decia:
> -/+u8                        turn on/off UTF-8 mode (implies wide-characters)

Entonces puse xterm -u8, me abrió otra ventana, pero cuando abrí el gaim-text y toqué "ñ" tuve el mismo error de antes :(

Además, me gustaría saber si alguien sabe como puedo hacerlo con xfce4-terminal en lugar de xterm, ya que es la terminal que uso por defecto.

---

### Post by nest on 2007-10-02
> **santiagoward2000 said:**
> Hola nest,
Perdoná mi ignorancia, pero cuando puse xterm -en me dio:


Después probé xterm -help, y entre todos los comandos que aparecen, vi uno que decia:


Entonces puse xterm -u8, me abrió otra ventana, pero cuando abrí el gaim-text y toqué "ñ" tuve el mismo error de antes :(

Además, me gustaría saber si alguien sabe como puedo hacerlo con xfce4-terminal en lugar de xterm, ya que es la terminal que uso por defecto.

si se te sigue colgando no va a ser tampoco esa la solución en la xfce4-terminal.

pero para saber como -y si se puede- hacer en esa consola pone xfce4-terminal -h o --help y te va a tirar algo parecido al mensaje que te dio la xterm.

---

### Post by santiagoward2000 on 2007-10-02
Si, revisé el "xfce4-terminal -h" y el "man xfce4-terminal", pero no dice nada sobre la codificacion de caracteres.

---

### Post by nest on 2007-10-02
> **santiagoward2000 said:**
> Si, revisé el "xfce4-terminal -h" y el "man xfce4-terminal", pero no dice nada sobre la codificacion de caracteres.

si no está en el man no creo que lo traiga incorporado. quizás hay alguna add-on extra por la net que te lo permita. pero ya estoy sobre hipótesis.

---

### Post by santiagoward2000 on 2007-10-02
> **nest said:**
> si no está en el man no creo que lo traiga incorporado. quizás hay alguna add-on extra por la net que te lo permita. pero ya estoy sobre hipótesis.

Ah, bueno, voy a empezar a buscar si encuentro alguno. Igual, gracias por la ayuda y la paciencia!!! :lolflag:

---

### Post by faktorqm on 2007-10-03
Hola muchachos, capaz vos esta opcion no la tenes, o no la viste no se. en ubuntu, voy a aplicaciones -> accesorios -> terminal.

voy a "terminal" (arriba en la barrita de archivo, edicion etc) y le doy a.....
"establecer codificacion de caracteres" y ahi me muestra, utf8 e iso 8859-15. y tambien me deja agregar. vos tenes esta opcion? salu2!

---

### Post by santiagoward2000 on 2007-10-03
> **faktorqm said:**
> Hola muchachos, capaz vos esta opcion no la tenes, o no la viste no se. en ubuntu, voy a aplicaciones -> accesorios -> terminal.

voy a "terminal" (arriba en la barrita de archivo, edicion etc) y le doy a.....
"establecer codificacion de caracteres" y ahi me muestra, utf8 e iso 8859-15. y tambien me deja agregar. vos tenes esta opcion? salu2!

No, en xfce4-terminal no la tengo... :(
Gracias igual

---

### Post by nest on 2007-10-04
> **faktorqm said:**
> Hola muchachos, capaz vos esta opcion no la tenes, o no la viste no se. en ubuntu, voy a aplicaciones -> accesorios -> terminal.

voy a "terminal" (arriba en la barrita de archivo, edicion etc) y le doy a.....
"establecer codificacion de caracteres" y ahi me muestra, utf8 e iso 8859-15. y tambien me deja agregar. vos tenes esta opcion? salu2!

si no me equivoco esa opción sólo sirve para las terminales de gnome, osea gnome-terminal.

---

### Post by faktorqm on 2007-10-04
weno, investigue en mi xubuntu. la respuesta estaba (como no podia ser de otra manera :P ) en el manual del xterm.
cuando apretas el boton que dice "help" en edit -> preferences te aparece un manual muy bonito en html y al final dice esto:

**_To switch between different encodings_**

[I]Terminal itself does not (yet) include builtin support for switching encodings on the fly in a terminal session. But since Terminal
implements an UTF-8 mode, you can use the Luit application to switch between different character encodings within a terminal session.[/I]

Ahi dice que tenes que usar la aplicacion "Luit" para cambiar entre codificaciones de caracteres. el link es:

[http://www.pps.jussieu.fr/~jch/software/luit/](http://www.pps.jussieu.fr/~jch/software/luit/)

En esa pagina te explica todo, asi que instalatelo y contame como te fue. La próxima: ¡¡no olvides leer el manual!! Salu2!!

---

### Post by santiagoward2000 on 2007-10-04
> **faktorqm said:**
> weno, investigue en mi xubuntu. la respuesta estaba (como no podia ser de otra manera :P ) en el manual del xterm.
cuando apretas el boton que dice "help" en edit -> preferences te aparece un manual muy bonito en html y al final dice esto:

**_To switch between different encodings_**

[I]Terminal itself does not (yet) include builtin support for switching encodings on the fly in a terminal session. But since Terminal
implements an UTF-8 mode, you can use the Luit application to switch between different character encodings within a terminal session.[/I]

Ahi dice que tenes que usar la aplicacion "Luit" para cambiar entre codificaciones de caracteres. el link es:

[http://www.pps.jussieu.fr/~jch/software/luit/](http://www.pps.jussieu.fr/~jch/software/luit/)

En esa pagina te explica todo, asi que instalatelo y contame como te fue. La próxima: ¡¡no olvides leer el manual!! Salu2!!

Hola, lamento decirlo, pero no me fue muy bien. Seguí las instrucciones, pero no conseguí cambiar al ISO 8859-15, solo puede usar el ISO 8859-1. El problema es que cuando quise abrir el gaim-text, se veia así:
[IMG]http://ubuntuforums.org/g/images/348163/medium/1_Screenshot-7.png[/IMG]

Pero tratando de ver el medio vaso lleno, toqué "ñ" y no se cerro! :lolflag:

---

### Post by santiagoward2000 on 2007-10-04
> **santiagoward2000 said:**
> Hola, lamento decirlo, pero no me fue muy bien. Seguí las instrucciones, pero no conseguí cambiar al ISO 8859-15, solo puede usar el ISO 8859-1. El problema es que cuando quise abrir el gaim-text, se veia así...

Pero tratando de ver el medio vaso lleno, toqué "ñ" y no se cerro! :lolflag:

Uhh, disculpen. No se que habra pasado, ahora se ve bien, pero el problema con la "ñ" sigue. Probe la ISO 8859-1 y la 8859-15, pero me aparece este error:
> Warning: couldn't find charset data for locale en_US.UTF-8; using ISO 8859-1.
Couldn't copy terminal settings


---

### Post by leo_rockway on 2007-10-05
yo probe con ut-8, 8859-1 y 8859-15; finch deja de funcionar en cuanto intento usar la ñ (de todas formas nunca la uso a la ñ porque tengo teclado estadounidense).

---

### Post by faktorqm on 2007-10-06
estoy medio enfermo, por eso te abandone. tenes los locale packs instalados?

language-pack-es
language-pack-es-base
language-support-es 

y tiene que haber uno mas (ahora no tengo mi xubuntu funcionando que deberia ser algo parecido a esto: language-pack-xfce-es, para buscarlo, escribi "aptitude search lang >> lan.txt" y eso te genera un archivo txt con la salida, despues haces "mousepad lang.txt" y ahi ves ke paquetes te faltan instalar)
sino tambien fijate si tenes instalados estos 3 para ver como se puede solucionar:

i   xterm                           - X terminal emulator                       
p   xtermcontrol                    - dynamic configuration of xterm properties 
p   xtermset                        - change the characteristics of an xterm 

(este es el resultado de la salida "aptitude search xterm")

bueno, no dejes de probar cosas y consultar. acordate ke toy medio enfermo. salu2!!!!!!!!!!!!!! ^_^

---

### Post by santiagoward2000 on 2007-10-06
> **faktorqm said:**
> estoy medio enfermo, por eso te abandone. tenes los locale packs instalados?

language-pack-es
language-pack-es-base
language-support-es 

y tiene que haber uno mas (ahora no tengo mi xubuntu funcionando que deberia ser algo parecido a esto: language-pack-xfce-es, para buscarlo, escribi "aptitude search lang >> lan.txt" y eso te genera un archivo txt con la salida, despues haces "mousepad lang.txt" y ahi ves ke paquetes te faltan instalar)
sino tambien fijate si tenes instalados estos 3 para ver como se puede solucionar:

i   xterm                           - X terminal emulator                       
p   xtermcontrol                    - dynamic configuration of xterm properties 
p   xtermset                        - change the characteristics of an xterm 

(este es el resultado de la salida "aptitude search xterm")

bueno, no dejes de probar cosas y consultar. acordate ke toy medio enfermo. salu2!!!!!!!!!!!!!! ^_^

Uhh, que bajón que estés enfermo!! Disculpá que te moleste, pero después de hacer "aptitude search lang >> lan.txt" y "mousepad lang.txt", se me abrió un archivo en blanco :confused:
Revisé en Synaptic y tengo los paquetes:
language-pack-es
language-pack-es-base
language-support-es 
Pero no encontré ninguno que se llame language-pack-xfce-es.
Si no podés contestar ahora no te preocupes. Espero que te mejores!

---

### Post by santiagoward2000 on 2007-10-06
Hola faktorqm,
¿Como estas? ¿Te sentis mejor?
Disculpa que te moleste. Pude abrir el archivo lan que cree. ¿Pero como se que paquetes me faltan?

---

### Post by faktorqm on 2007-10-08
si perdona, me ekivoke yo. al final tenias ke escribir mousepad lan.txt y listo.
te das cuenta por que a la izquierda tienen una i (letra i minuscula) y los que no tenes instalados te aparecen como p. (si haces "man aptitude" te dice ahi que es cada letra) salu2!!

---

### Post by santiagoward2000 on 2007-10-14
Hola faktorqm, ¿como estas? ¿mejor?
No había podido ver antes lo que me dijiste, porque estaba hasta las manos con la facu. Aprovecho ahora que tengo algo de tiempo, jeje.
Los paquetes que encontre que me faltan instalar son:
[LIST]
[*]texlive-lang-spanish
[*]language-pack-gnome-es
[*]language-pack-gnome-es-base
[*]language-pack-kde-es
[*]language-pack-kde-es-base
[*]sword-language-pack-es
[/LIST]
Yo supongo que no deben ser los paquetes de kde y gnome, pero no se que sean  los de texlive y sword. ¿Puede que sean esos?

---

### Post by Daishiman on 2007-10-14
Más allá de todo, no se olviden de abrir el reporte de bug con la gente de Gaim/Pidgin.

---

### Post by santiagoward2000 on 2007-10-15
> **Daishiman said:**
> Más allá de todo, no se olviden de abrir el reporte de bug con la gente de Gaim/Pidgin.

Hola Daishiman,
Traté de reportarlo, pero en la página de pidgin no encontré dónde. Sabés dónde hacerlo?

---

### Post by faktorqm on 2007-10-16
aca hay un chabon que bate la justa de las justas:

[http://www.maruko.ca/i18n/](http://www.maruko.ca/i18n/)

si te sigue sin andar avisa. salu2! (ya me cure :D)

---

### Post by santiagoward2000 on 2007-10-16
> **faktorqm said:**
> aca hay un chabon que bate la justa de las justas:

[http://www.maruko.ca/i18n/](http://www.maruko.ca/i18n/)

si te sigue sin andar avisa. salu2! (ya me cure :D)

Hola faktorqm,
Qué suerte que te curaste!! (Así te puedo seguir molestando tranquilo :lolflag: )
Estuve probando lo que dice ese tipo. Traté de abrir xterm usando:
> xterm -u8
y me tiró el mismo error.
Después traté de cambiar mi teclado a UTF usando:
> export LANG=es.UTF-8
pero también se cerró. :(

---

### Post by faktorqm on 2007-10-19
che, y si instalas la terminal de gnome? kiero creer que no vas a tener ningun drama......

```
sudo apt-get install gnome-terminal gnome-terminal-data
```

proba eso y fijate que onda. salu2!

---

### Post by santiagoward2000 on 2007-10-22
> **faktorqm said:**
> che, y si instalas la terminal de gnome? kiero creer que no vas a tener ningun drama......

```
sudo apt-get install gnome-terminal gnome-terminal-data
```

proba eso y fijate que onda. salu2!

Hola faktorqm,
Disculpá que te deje medio colgado, es que hace poco instalé Gusty, y ahora estoy tratando de hacer que ande todo. Cuando tenga un rato instalo Finch y Gnome-Terminal y te cuento....
Gracias!!

---

### Post by santiagoward2000 on 2007-10-25
> **faktorqm said:**
> che, y si instalas la terminal de gnome? kiero creer que no vas a tener ningun drama......

```
sudo apt-get install gnome-terminal gnome-terminal-data
```

proba eso y fijate que onda. salu2!

Hola faktorqm,
Mirá, instalé gnome-terminal, y tampoco pude. Si uso UTF-8 tengo el mismo problema (se cierra a penas toco la "ñ"). Si lo pongo como ISO-8859-15, la "ñ" no se escribe cuando la toco,no se cierra al toque, me deja un espacio, pero se cierra después de darle enter, con em mismo error:
```
Segmentation fault (core dumped)
```

---

### Post by faktorqm on 2007-10-26
hola, estuve leyendo banda de cosas. me calente y lo abri desde mi xubuntu. en mi caso, sin tocar nada, basta con apretar la "ñ" para que se cierre todo, tendria que ver como ver el error que tira :S

Lei 2 cosas que me llamaron la atención mas puntualmente:

La primera, es que ese programa utiliza emulación de terminal, y que se puede determinar. Creo que por defecto esta la vt200, entonces habria que ver si cambiandola a vt100 o vt110 arranca. 

La segunda es que el programa este utiliza tambien de "trasfondo" digamos, la biblioteca ncurses. ncurses es una biblioteca heredada de "curses" de unix, (ncurses significa "new curses", más información escribir "man ncurses" en una terminal ;) ) y ésta biblioteca funciona con un charset distinto al de la terminal, y POR DEFECTO IGNORA el charset asignado en la terminal, por lo tanto tendriamos que primero cambiar el charset de ncurses, y recien ahi vamos a estar seguros.

Otra cosa que vi, es que hay un archivo de configuracion que tiene unas teclas que estan re mapeadas. por ejemplo, la tecla para arriba, o la tecla para abajo, y la barra espaciadora (ver "man gaim-text"). Con esto: no seria novedoso poner que cada vez que apretas la letra "ñ" te mapee en el charset que usa el programa la letra "ñ"? la única excepcion a esto es que si efectivamente la "ñ" no esta en el charset por defecto del programa, el programa revienta igual que lo hace ahora y tenemos que terminar si o si en cambiar el charset del programa o de la interfaz sobre la que corre.

Bueno, reportaste el bug? salu2!!

---

### Post by santiagoward2000 on 2007-10-26
Hola,
Jeje, disculpá que te estoy haciendo laburar tanto!
> **faktorqm said:**
> Bueno, reportaste el bug?
Una pregunta, ¿dónde lo reporto?
Gracias, saludos

---

### Post by faktorqm on 2007-10-26
aca: no se si te tendras que registrar o algo

[http://developer.pidgin.im/wiki/BugTracking](http://developer.pidgin.im/wiki/BugTracking)

leete "man gaim-text" y "man ncurses" y me contas si sacas algo en limpio., yo te aviso por mi parte a ver que sale. salu2!

---

### Post by santiagoward2000 on 2007-10-26
> **faktorqm said:**
> aca: no se si te tendras que registrar o algo

[http://developer.pidgin.im/wiki/BugTracking](http://developer.pidgin.im/wiki/BugTracking)

leete "man gaim-text" y "man ncurses" y me contas si sacas algo en limpio., yo te aviso por mi parte a ver que sale. salu2!

Bueno faktorqm, ya lo reporté. Cuando tenga tiempo me leo los "man" y veo que saco. Ahora me tengo que poner a estudiar, tengo un parcial mañana JAJA.

---

### Post by santiagoward2000 on 2007-10-28
> **santiagoward2000 said:**
> Bueno faktorqm, ya lo reporté. Cuando tenga tiempo me leo los "man" y veo que saco. Ahora me tengo que poner a estudiar, tengo un parcial mañana JAJA.

Bueno, me contestaron el reporte y me pidieron que si uso el Pidgin 2.2.2, genere un backtrace y se los mande. Como con Gusty viene el 2.2.1, primero tuve que compilar el nuevo. Lo hice, abrí el Finch, y probé si seguía teniendo el problema. Se sigue cerrando, pero ya no me pone ningún error. Generé el backtrace, y este solo dice que el finch "exited normally". Igual se los mandé, a ver qué me dicen.
Sobre el man, todavía no lo leí, voy a ver si me pongo esta noche :)
Cuando me contesten les cuento,
Saludos

---

### Post by faktorqm on 2007-10-29
yo lo que no entiendo de los man es que hace referencia a entradas en archivos.... que no existen!! no se si t diste cuenta de eso, yo los buske y no encontre ninguno, y entonces los cree a mano pero no paso nada. (en las ubicaciones que decia el man estamos de acuerdo) asi que bueno nada, no importa que diga el backtrace, capaz se dan cuenta y lo arreglan! salu2!

---

### Post by santiagoward2000 on 2007-11-05
Bueno gente, por fín me contestaron el bug report, pero me dicen que el backtrace no sirve (ya lo suponía porque decía que se cerró con normalidad) y que no pudieron reproducir el problema.
¿A alguien se le ocurre qué se puede hacer, para generar un backtrace que sirva?

---

### Post by marianom on 2007-11-07
¿Con qué comandos lo generaste ¿Cuando compilaste, lo hiciste con las opciones de debug?

---

### Post by santiagoward2000 on 2007-11-08
> **marianom said:**
> ¿Con qué comandos lo generaste ¿Cuando compilaste, lo hiciste con las opciones de debug?

Hola Mariano!
Primero traté de usar las instrucciones en el [wiki]("https://wiki.ubuntu.com/Backtrace") sin tenerlo ya abierto, pero como vi que se corria en la misma terminal y se me mezclaba todo, busqué el PID y lo abrí en una terminal separada.

> Make sure the GNU Debugger is installed. 
sudo apt-get install gdb

Find the process ID of <program>: 
pidof <program>

Start gdb: 
gdb 2>&1 | tee gdb-<program>.txt
(gdb) handle SIG33 pass nostop noprint
(gdb) set pagination 0
(gdb) attach <PID>

(If the program is running as root, use sudo gdb instead of just gdb above.)

Continue the <program>: 
(gdb) continue

The program will continue running. Perform any actions necessary to reproduce the crash 

Retrieve a backtrace of the crash: 
(gdb) backtrace full
(gdb) info registers
(gdb) thread apply all backtrace
(gdb) quit

Attach the complete output from GDB, contained in gdb-<program>.txt, in your bug report. 

Note that you can also set logging to a file like this: 
(gdb) set logging file gdb-<program>.txt
(gdb) set logging on

Como eso decía que el programa finalizó con normalidad, en la Bug Report de pidgin.im me dijeron que pruebe:
> How about, after attaching to the process, you do 'break _exit', then 'continue', if you press the key after that, does it break in gdb, with a useful backtrace?

Pero cuando hice eso y toqué "ñ", el finch se cerró, pero el backtrace decía que seguía abierto.

---

### Post by santiagoward2000 on 2007-11-11
Hola!
Bueno, recién se me dio por hacer una prueba. Toqué Ctrl+Alt+F2 y abrí el finch directamente en el Bash. Probé si ahí se repetía el error y... NO! Ahí anda sin problema!!
Como no entiendo mucho de esto, ¿alguien sabe qué input usa, o qué diferencia hay entre usar directmente Bash y xfce4-terminal?

---

### Post by santiagoward2000 on 2008-01-14
Bueno gente!
Después de pelearme con esto por 3 meses, encontré una solución!!!
Probé poner: ```
TERM=screen
``` antes de abrir finch, y ahora anda la "ñ"!
Ahora voy a tener que volver a acostumbrarme a usarla de nuevo...

---

