---
title: "Dudas con Xubuntu"
date: 2007-08-09
forum: Argentina Team
---

### Post by faktorqm on 2007-08-09
Hola a to2!, tengo un pc-chips 810 LMR, con un AMD Duron 900Mhz, placa de video SiS 630 integrada de 16MB, con 256MB de RAM y 80gb de disco y una lectora. Resulta que me baje el xubuntu 7.04 alternate cd, lo kemé, lo instale todo ok, arranque todo ok. Ahora bien, tuve varios problemas que paso a enumerar:

1) El apt-get se queda colgado. Ocurre lo siguiente, escribo sudo apt-get update y  en un momento se queda en: [99%] Esperando cabeceras. Y no pasa naranja.
Entonces quise instalar algo y cada vez que escribo apt-get vuelve a tratar de bajar las cabeceras. solucion? se cayeron los servidores ayer? nunca me habia pasado esto :(

2) Los discos (Lectora y disco IDE) me los toma como scsi. a mi no me molesta, pero por curiosidad no mas queria saber por que pasaba esto.

3) El entorno gráfico, XFCE4 anda bien, pero no me gusta la velocidad. Tengo que reconocer que el 98SE andaba mas rapido, por mas que no me guste. Asi que tengo pensado cambiar: o me instalo DSL (Damn small Linux) o sino dejo el xubuntu y cambio a Fluxbox como manejador de ventanas. Que me recomiendan?

4) Xubuntu al igual que ubuntu carga al inicio 7000 cosas que no voy a usar. y estoy buscando rendimiento. Habian posteado en algun lado una guia para poder sacar eso. Alguien me haría el favor de volverla a postear? sinceramente no la encuentro.

5) Hay algo mas liviano que el firefox? por que abro mas de 7 paginas y se empieza a poner tieso el duron XD. puede ser el switfox? alguien me recomienda otro?

Muchas gracias a todos. Nos vemos!

---

### Post by facundocorradini on 2007-08-09
hola  faktorqm

Te respondo con lo poco que conosco al Xubuntu...

1) pudiste bajar algo o te pasó eso desde la primera vez?

2) Querrás decir que te los muestra como SDA1 y así? a mi me pasa lo mismo cuando actualicé de 6.10 a 7.04, pero nunca me causó ningún problema.   Leyendo por ahí me encontré con q esto tiene q ver con algunas cuestiones de los kernel nuevos, que han cambiado la denominación para ciertos tipos de IDE. Igualmente mucho no investigué....

3) Personalmente te recomiendo quedarte con ubuntu e instalar un nuevo escritorio. Aunque me resulta raro que tengas problemas de velocidad: yo tengo una maquina aún mas humilde y no he tenido problemas. 
En cuanto a los escritorios, si te gusta la VELOCIDAD, te recomiendo enlightenment. La versión 16 es muy buena, y la 17 es increible, pero esta última aún está en desarrollo. Si te interesa te paso un tutorial para instalarlo.

4) Mmm.. realmente no creo que encuentres mucha diferencia en rendimiento. tal vez tengas algún cambio en la velocidad de arranque, pero te recomendaría dejar las cosas como están...  anyway, creo q el tuto que buscás es este: [http://www.ubuntu-es.org/node/4440](http://www.ubuntu-es.org/node/4440)

5) 1- nunca subestimes la potencia de un duron...  2- El swiftfox es igual de pesado q el firefox. Yo con tu sistema me quedaría con FF, pero bueno... eso pq soy Firefox-dependiente... no conosco browsers más livianos...

---

### Post by valucha on 2007-08-09
[COLOR="DarkOrchid"]Para un navegador más liviano usá el Opera. Es excelente.[/COLOR]

---

### Post by marianom on 2007-08-09
Más ligero que [Dillo]("http://en.wikipedia.org/wiki/Dillo") no existe (tampoco trae mucho que digamos).

Bueno, está Lynx pero no creo que te guste mucho.

---

### Post by facundocorradini on 2007-08-09
> **marianom said:**
> Más ligero que [Dillo]("http://en.wikipedia.org/wiki/Dillo") no existe (tampoco trae mucho que digamos).

Bueno, está Lynx pero no creo que te guste mucho.

Disculpame mariano, pero creo que te fuiste a un extremo medio exagerado.  Lo que  faktorqm quería es (a mi entender) un navegador liviano pero que tenga todo lo necesario para un usuario "comun"

Dillo no soporta CSS ni Javascript...
y Lynx es un navegador en modo texto (se usa en consola)...


Yo recomendaría simplemente usar Firefox, y tenerle un poquito de paciencia...

---

### Post by marianom on 2007-08-09
Yo uso Dillo bastante: por temas laborales tengo que recurrir varias veces al día a documentación de los lenguajes de programación que uso y la mayoría de la data está en html. Una sesión de Dillo no se siente en la máquina. IMHO, ese es su nicho y si faktor necesita  cubrir una actividad similar, yo le sugiero que lo considere (y, de todos modos, ahí nomás le aclaro que mucho no trae plus él mencionó DSL y es el navegador por defecto que trae + Firefox).

Con respecto a lynx, es más fuerte que yo rendirle tributo: varias veces he estado atrapado en las más abyectas de las terminales, sin otra opción y con un error de configuración que solo en internet podía salvar. EL buen lynx me prestó una ayuda invalorable en esos momentos.

[OT]: Facundo, tu nombre me suena de algún lado y yo también soy marplatense: ya la memoria volverá en algún momento y veremos si estoy en lo cierto.

---

### Post by facundocorradini on 2007-08-10
Jaja...La verdad que tener lynx me ha salvado la vida  más de una vez.. (sobre todo cuando destrozé el X experimentando...)

Y a dillo lo usaba antes de descubrir un par de plugins de firefox, para ver que tan bien se ven mis sitios sin... todas esas cosas q hacen que se vea bien un sitio.

La verdad es que tenés razón. Ambas herramientas son muy útiles para quienes trabajamos en estas cosas... 

[OT] viendo tu perfil me dió la misma sensación, pero mi memoria es bastante mala...

---

### Post by AnRa on 2007-08-10
> **marianom said:**
> Más ligero que [Dillo]("http://en.wikipedia.org/wiki/Dillo") no existe (tampoco trae mucho que digamos).[xlinks2](http://links.twibright.com/) ;)

---

### Post by faktorqm on 2007-08-11
Bueno gracias a todos. 

Lynx me salvó las papas del fuego más de una vez, así que no lo bardeen, les cuento más, con el lynx bajé el envy, para poder instalar el driver de nvidia por que no tenia interfaz gráfica. mi mayor proeza linuxera!

Opera lo usé en windows, lo probé en linux pero tiene tooooodos los problemas. Hasta que la ***** de adobe no se digne a sacar su ****** de programas para opera y/o linux, se van a ver la mitad de las cosas hasta ese entonces.

Dillo me gustó, lo voy a probar al igual que xlinks2. 

El tema del apt-get lo solucioné, pero no sé como. Perdon por no poner el feedback, pero hice muchas cosas y no sé cuál realmente es la que hizo que anduviera.

Voy a hacer una cosa, voy a poner dsl (Damn small linux, no digital subscriptor (o era suscriber?) line xDXD) en otra partición, así tengo los dos y comparo. Mi idea era como alguien dijo por ahí, que el explorador no te "mate" la compu, pero tener las funcionalidades comunes. Yo sé que es mucho pedir para el hardware, pero el Duron es una masa, es eterno, y le puse un disipador+cooler para un athlon xp 1800 y lo overclokie a 1.200 mhz. y está super frio ahora. :-)

Ví por ahí que varios no bancan CSS. no sé qué es, pero sé que es algo de hoja de estilos. Es muy decisivo que no banque eso a la hora de ver clarin.com? por ejemplo. Por que capaz yo veo eso y como no sé que es pienso que es malo y capaz nada ke ver xD.

Algo para reflexionar: Si se activa el salvapantallas anda todo ok, cuando quiero volver se me cuelga el escritorio y le tengo ke dar a ctrl + alt  backspace para que vuelva. Cuando vuelve se me cuelga la pc. Ideas? Sugerencias? me estoy llevando a las patadas con Xubuntuuuuuuuuuuuuuuuu!!!!!!!!!!!!! :(

Lo ultimo: salió acetoneiso 2, para los amantes del alcohol 120%. Esta muuuuuy bueno. Recomiendo se peguen una vuelta por el site. [http://www.acetoneteam.org/](http://www.acetoneteam.org/)

---

### Post by facundocorradini on 2007-08-11
> **faktorqm said:**
> Bueno gracias a todos. 

Lynx me salvó las papas del fuego más de una vez, así que no lo bardeen


 Nadie lo bardeó, todos lo veneramos.

> 
 Yo sé que es mucho pedir para el hardware, pero el Duron es una masa, es eterno, y le puse un disipador+cooler para un athlon xp 1800 y lo overclokie a 1.200 mhz. y está super frio ahora. :-)


No entiendo bien la preocupación... yo tengo una maquina corriendo Xubuntu... Es una VIA de 500mhz (para que se den una idea el procesador no trae ni cooler),128mb de ram pc133... y aún así me anda todo más que bien... 
Y el duron es mil veces más procesador que el "via samuel 3"...

... Y ni hablar del pentium 233 ...  que se jubiló para pasar a ser el mejor router que se puede conseguir.... 
> 
Ví por ahí que varios no bancan CSS. no sé qué es, pero sé que es algo de hoja de estilos. Es muy decisivo que no banque eso a la hora de ver clarin.com? por ejemplo. Por que capaz yo veo eso y como no sé que es pienso que es malo y capaz nada ke ver xD.


CSS significa hojas de estilo en cascada, mejor conocido como "lo que hace que un sitio se vea como algo más que texto". 
para que te des una idea, sin CSS todos los sitios se ven como este:
[http://tille.garrels.be/cyberfeministe/HOWTO/f35.html](http://tille.garrels.be/cyberfeministe/HOWTO/f35.html)

En cuanto a Clarin.com, lo acabo de probar y no veo q tenga problemas al desactivar los css... por ahí te trae problemas el no tener javascript, ya que tiene muchas cosas basadas en este.
Lo del CSS puede ser un problema, por ejemplo, en Gmail u otros sitios de complejidad parecida.

---

### Post by jpmorelli on 2007-08-11
> **faktorqm said:**
> 

3) El entorno gráfico, XFCE4 anda bien, pero no me gusta la velocidad. Tengo que reconocer que el 98SE andaba mas rapido, por mas que no me guste. Asi que tengo pensado cambiar: o me instalo DSL (Damn small Linux) o sino dejo el xubuntu y cambio a Fluxbox como manejador de ventanas. Que me recomiendan?



Tené en cuenta que estás usando un Sist. Operativo del 2007 contra uno del 98, cuál recomendarías vos ? Suerte !:lolflag:

---

### Post by kowal on 2007-08-13
Te tiro algunos tips sobre experiencias que tuve tratando de revivir PCs "obsoletas":

- Si vas a instalar un derivado de Ubuntu.. instalá la versión Server (o una ISO "barebones" de [acá](https://help.ubuntu.com/community/Installation/MinimalCD)) y de ahí le instalas:

xorg, opera, xdm, fluxbox (o icewm o xfce o enlightenment u openbox), rox-filer (o thunar), centericq (o gaim).. etc.

XFCE puede ser ágil, pero parece que el de Xubuntu viene medio cargadito. 
Entre los browsers para PCs "viejas" me quedo con Opera, porque además de ser muy liviano.. viene completo: tiene incorporado lector de RSS, cliente de correo, cliente para bittorrent, etc.

También te recomiendo que le pegues una leída a [esta](https://help.ubuntu.com/community/Installation/LowMemorySystems) entrada del wiki de Ubuntu donde hay varias configuraciones "minimas".

- Otra sería hacer lo mismo, pero con Debian 4 (puede haber una mejoria en el rendimiento)

- Usarla de [Thin Client](http://es.wikipedia.org/wiki/Thin_client) ("terminal boba") aprovechando otra PC "mejor" con Linux que le haga de servidor a través del protocolo NX. Para mi esta es la mejor opción que encontré.

Cualquier duda, preguntá ;)

Saludos!

---

### Post by faktorqm on 2007-08-13
Muchas gracias!!!!! Pruebo con eso. El tema principal es ese, viene bastante cargadita, yo pense que iba a andar un poco mas rapido, pero ya de por si tiene banda de cosas al inicio, que las vole con el sysv-rc-conf. 
Che, y con el opera, podes ver flash/shockwave? Yo en 6.06 no pude. Gracias por todo!

---

### Post by lavaramano on 2007-08-13
shockwave para linux no hay, lo podes usar si corres un browser de windows con wine.
medio cabesa, pero funca de 1o.

---

### Post by faktorqm on 2007-08-13
ok, igual iba medio con trampa la pregunta, en realidad para opera en windows no hay shockwave, asi que menos va a haber para linux, pero viste como son estas cosas, capaz alguno se tomo el trabajo y bue....
Salu2!!

---

