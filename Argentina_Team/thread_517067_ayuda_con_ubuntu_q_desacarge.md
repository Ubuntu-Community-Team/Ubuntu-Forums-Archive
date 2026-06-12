---
title: "ayuda con ubuntu q desacarge"
date: 2007-08-04
forum: Argentina Team
---

### Post by edd12river on 2007-08-04
me baje de esta pagina el ubuntu live cd, grabe el rar en el cd y puse q butee del mismo y no funciono, descmprimo el archivo y grabo en otro cd  los archivos y tampoco butea, q hago mal? es live cd de verdad?...


desde ya muchas gracias

---

### Post by juanman on 2007-08-04
Lo q bajaste es una imagen iso de cd. No la abras con winrar! Sino q graba el cd directamente con nero (o el programa de grabacion de cds q uses) desde la opcion grabar imagen de cd guardada en disco o algo parecido...

---

### Post by guillermolisi on 2007-08-04
Si grabas la imagen ISO con WinRAR no generas la informacion necesaria en el CD para que este sea booteable. Es como haber hecho un CD con datos solamente.
Hace como te dijo juanman.

---

### Post by edd12river on 2007-08-04
listo, ya funciona, pero no tiene compatibilidad con mi mouse, q es ps2(o com osea), puse uno minidimm pero q no le funciona el click izquierdo, ademas de eso, me dijeron q para q reconozca el modem, escriba en un terminal ppoeconf o pppoeconfig, pero me dice q no lo encuentra, nose q hacer...

---

### Post by Darth Trix on 2007-08-04
Se que me van a banear seguro con este post, pero no creo que Linux sea lo mejor para vos si no sabes grabar una **** imagen de CD.

Con onda, no lo tomes a mal.

---

### Post by Hei Ku on 2007-08-04
> **Darth Trix said:**
> Se que me van a banear seguro con este post, pero no creo que Linux sea lo mejor para vos si no sabes grabar una **** imagen de CD.

Con onda, no lo tomes a mal.
@Darth Trix:
En realidad, demostro que sabe preguntar y aprender de sus errores, asi que puede ser que linux sí sea para él. 

Todos tenemos lagunas en nuestro conocimiento, no es algo malo, si sabemos cómo solucionar eso en el momento oportuno. Y creo que el espiritu de este foro es ayudar a la gente a utilizar linux. Eso incluye enseñar a grabar una imagen de CD y muchas otras cosas. Me parecio muy desconsiderado tu comentario.


@edd12river:
Mas en tema, el mouse PS2 debería reconocerlo. Yo tenia uno asi hasta hace poco, seguramente alguien tiene experiencia en ese tema.

Para instalar el pppoeconf seguramente tengas que estar conectado a internet, lo cual es un problema, porque no tenes el modem instalado, no? Te sugiero que busques primero si tu modelo de modem esta soportado. Los drivers de modems no son algo que se luzca en Linux, pero podes tener suerte.

---

### Post by edd12river on 2007-08-04
si, se grbar un cd, pero no puse grabar imagen sino q grabe el archivo q descarge...no tenes xq creertela, cualquiera tiene un deslis...= no vengo  peliar, sino a tartar de poder usar linux, ya q me parece muy bueno, si, el mouse nose q paso...probare de nuevo, yo pedi los cd's, pero me lo baje para probar q toda mi pc sea compatible, y en su defecto tratar de soluciuonarlo antres de instalarlo definitivamente...probare lo del modem, segun speedy es compatible con linux, pero nunca se sabe, no saben mucho los q te atienden por telefono...

gracias ^^.... y espero solucionar mi problema

---

### Post by edd12river on 2007-08-04
probe, pero sige sin reconocerme el mouse, sera xq es live cd?, osea no l oinstale todavia, reconoce todo, el sonido, el modem no pude probar, y q no puedo acceder a ningun lado x el tema del mouse...si es xq el live cd lo instalo, pero queria instalarlo del cd q me manden, no del q grabe yo

---

### Post by Hei Ku on 2007-08-04
la mayoria de nosotros lo instalamos desde el cd bajado de internet, aunque te recomendaria que en ese caso uses el Alternate CD. Aunque es en modo texto, es igual de claro, pero anda mejor.

En cuanto al mouse, es raro, pero encontre reportes similares. Necesitaria que me des un par de datos:
- modelo del mouse
- modelo del modem (hay varios tutoriales pero varian de acuerdo al modem ADSL que sea)
- contenido del archivo /etc/X11/xorg.conf

Si bien no vas a poder hacer mucho mientras sigas sin instalar, por lo menos ya vas sabiendo que problemas te podes encontrar al hacer la instalacion definitiva.

---

### Post by edd12river on 2007-08-04
el mouse es un biwal, nose q datos nesesitas de el,
modem speedtouch tomson 330 usb
lo del archivo, nose como verlo...sin mouse es ***** hacer algo..pero vere si puedo verlo, desde donde lo veo?

---

### Post by guillermolisi on 2007-08-04
edd12river

Te cito mas abajo un post que envie en la lista Ubuntu-ar no hace mucho tiempo en relacion al modem ADSL Speedtouch. No se que resultado tuvo mi ayuda en ese thread, pero tal vez sea de utilidad.en tu caso.

> 
De: Guillermo Lisi <[EMAIL="unimix@fibertel.com.ar"] unimix@fibertel.com.ar[/EMAIL]>
Para: [EMAIL="almafuerte26506@yahoo.com.ar"]almafuerte26506@yahoo.com.ar[/EMAIL]
CC: [EMAIL="ubuntu-ar@lists.ubuntu.com"] ubuntu-ar@lists.ubuntu.com[/EMAIL]
Enviado: domingo 27 de mayo de 2007, 18:28:04
Asunto: Re: ubuntu-ar [Contacto] internet

Hola Roberto

Como para saber desde donde arrancamos, tenes manuales del Speedtouch ? 
Si no, te paso el siguiente vinculo que estimo te sera de gran ayuda:

[http://www.adslzone.net/alcatel.html](http://www.adslzone.net/alcatel.html)

Fijate que, ademas de las caracteristicas del equipo y su instalacion, te muestra como configurarlo y hasta hay tutoriales en PDF. 

Y si con esto no alcanza hay un vinculo en esa pagina que te lleva a un foro especifico (al cual no entre).  

Espero te sirva, por lo menos como para empezar.

Saludos


---

### Post by Hei Ku on 2007-08-04
Apreta alt+F2, eso te hace aparecer el dialogo de comando.

ahi pone:sudo gedit /etc/X11/xorg.conf

copia y pega el contenido del archivo

---

### Post by edd12river on 2007-08-04
che aprete alt+f2, y puse ok, y aparece en blanco lo q se abre...eso es malo no??...y l de arriba, ahi no encontre nada, postie en el foro, pero no obvtuve repsuesta todavia, grax =


**edit**: el mouse es serie, no ps/2..perdon

---

### Post by Hei Ku on 2007-08-05
En esta thread dan un poco de ayuda sobre el problema con los mouse serie; [http://ubuntuforums.org/showthread.php?t=2661](http://ubuntuforums.org/showthread.php?t=2661)

En principio se trata de editar el xorg.conf

Podes probar lo siguiente: CTRL+ALT+F1

Te va a aparecer una pantalla de terminal (no te asustes!!! :D )

si estas usando el liveCD, deberias ya estar logueado como root, asi que pone lo siguiente:

pico /etc/X11/xorg.conf

Te deberia aparecer un editor de texto, con el contenido del archivo.
En la seccion que dice:

       Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ImPS/2"

cambiala por:
        Option          "Device"                "/dev/ttys0"
        Option          "Protocol"              "Auto"

Es una prueba, no se como funcionara con el LiveCD, pero algo similar deberias hacer al  instalarlo definitivo.

Si te aparece algun error, necesito saber en que paso, y que mensaje de error te da. Recorda que en Linux los errores TIENEN sentido y SON DE AYUDA.

---

### Post by edd12river on 2007-08-05
bueno paso a explicar, la explicacion es corta:

abri el terninal como me dijiste, pongo pico/etc/x11/xorg.conf


y me salta este error, archivo no encontrado 0 directorios, o algo asi...seguro es porque es livecd...tengo pensado en la semana hacerle lugar al ububtu e instalarlo... y usar los 2 sistemas operativos juntos, y bue, luego borrar el vista (ya q es el sistema operativo q tengo) y dejar el ubuntu....

---

### Post by Hei Ku on 2007-08-05
pregunta que puede parecer tonta, pero bueno, mejor confirmar:

pusiste:
pico /etc/X11/xorg.conf

o

pico/etc/X11/xorg.conf    (sin espacio entre pico y el nombre del archivo)


De todas maneras, si estan convencido de darle una oportunidad, te recomiendo que lo instales y seguimos viendo el tema en el sistema ya instalado, que va a ser mas facil. Como te dije antes, mi recomendacion es que te bajes el Alternate CD y lo instales desde ese. El LiveCD es mas grafico, pero el otro anda mejor generalmente, y es mas rapido.

---

### Post by edd12river on 2007-08-05
> **Hei Ku said:**
> pregunta que puede parecer tonta, pero bueno, mejor confirmar:

pusiste:
pico /etc/X11/xorg.conf

o

pico/etc/X11/xorg.conf    (sin espacio entre pico y el nombre del archivo)


De todas maneras, si estan convencido de darle una oportunidad, te recomiendo que lo instales y seguimos viendo el tema en el sistema ya instalado, que va a ser mas facil. Como te dije antes, mi recomendacion es que te bajes el Alternate CD y lo instales desde ese. El LiveCD es mas grafico, pero el otro anda mejor generalmente, y es mas rapido.

jeje, q ****** :P...bue no me di cuenta del espacio...:P, voy a probar y dejo bajando el alternate cd... depsues te cuento

---

### Post by edd12river on 2007-08-05
hice eso, pero aparece en blanco...osea no me aparece nada escrito...probe con los comandos q dice abajo, puse buscr y escribi /dev/input/mice y no aparece nada... :(, ya toy bajando el alternate cd

---

### Post by MeduZa on 2007-08-06
ya son varios los que veo que hacen esto, desarman el iso con el winrar y graban los datos :P
y despues no le andan los cd, a uno le trate de esplicar, rompio 2 cd antes de hacerlo bien
primer intento: saco todo del rar y lo grabo
segundo intento: grabo el iso en un cd (solo el archivo .iso en un cd)
la tercera vez supo como graba la imagen en un cd :P

---

### Post by faktorqm on 2007-08-06
El problema es que apretan siguiente siguiente siguiente y no saben lo que hacen. no se lo tomen a mal pero es asi y lo saben, asi que no digan que no. 
Winrar cuando lo instalas, en la ultima pantalla te muestra todas las asociaciones a los archivos. Es cuestion de tomarse el trabajo de leer un poquito y pensar que es lo mejor, si asociar .iso a winrar o a un programa mejor como ultraiso. (por ejemplo) tambien te asocia .zip por ejemplo, y vi en muchas pero en muchas computadoras que tienen el winZip y el winrar con windows xp. o sea, tienen 3 manejadores de archivos .zip e ignoran totalmente sobre el tema.
edd12river: obviamente esto no es para vos, me parece perfecto que preguntes TODO lo que necesites, por que yo tambien la pase, antes no sabia nada de nada. (3 años aprox) y preguntaba absolutamente todo, hasta para que servia ls.
Aca en este foro estamos para responder lo que vos necesites, en la medida de que lo sepamos, obviamente. No sabes grabar un iso? abri el nero, archivo -> abrir, elegi la iso y apreta grabar a la velocidad que mas te guste. Era simple la respuesta no? Me parece que estan de sobra otro tipo de comentarios. ok?
Espero que no pierdas el espiritu de preguntar, y las ganas de usar GNU/Linux. No importa si haces preguntontas, lo importante es que preguntes. "No es sabio aquel que cree que sabe, sino es sabio el que sabe que no sabe". (lo aprendi en pensamiento cientifico de la uba en el cbc XD) Salu2!!

---

### Post by edd12river on 2007-08-06
> **faktorqm said:**
> El problema es que apretan siguiente siguiente siguiente y no saben lo que hacen. no se lo tomen a mal pero es asi y lo saben, asi que no digan que no. 
Winrar cuando lo instalas, en la ultima pantalla te muestra todas las asociaciones a los archivos. Es cuestion de tomarse el trabajo de leer un poquito y pensar que es lo mejor, si asociar .iso a winrar o a un programa mejor como ultraiso. (por ejemplo) tambien te asocia .zip por ejemplo, y vi en muchas pero en muchas computadoras que tienen el winZip y el winrar con windows xp. o sea, tienen 3 manejadores de archivos .zip e ignoran totalmente sobre el tema.
edd12river: obviamente esto no es para vos, me parece perfecto que preguntes TODO lo que necesites, por que yo tambien la pase, antes no sabia nada de nada. (3 años aprox) y preguntaba absolutamente todo, hasta para que servia ls.
Aca en este foro estamos para responder lo que vos necesites, en la medida de que lo sepamos, obviamente. No sabes grabar un iso? abri el nero, archivo -> abrir, elegi la iso y apreta grabar a la velocidad que mas te guste. Era simple la respuesta no? Me parece que estan de sobra otro tipo de comentarios. ok?
Espero que no pierdas el espiritu de preguntar, y las ganas de usar GNU/Linux. No importa si haces preguntontas, lo importante es que preguntes. "No es sabio aquel que cree que sabe, sino es sabio es que sabe que no sabe". (lo aprendi en pensamiento cientifico de la uba en el cbc XD) Salu2!!

grax loco! al fin alguien q piensa antes de hablar(no lo digo por todos), ademas trate de grabar el cd a las 4 am...jeje...ahora va todo bien, = tengo q comprarme un mouse...pero bue, y el tema del modem de speedy es tremendamente largo lo q hay q hacer...y con mi 0 experiencia en linux me parece q voy a dejar el xp por un tiempo...pero bue! grax loco!...

---

