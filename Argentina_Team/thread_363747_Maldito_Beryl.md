---
title: "Maldito Beryl"
date: 2007-02-17
forum: Argentina Team
---

### Post by matog on 2007-02-17
Instalé Beryl siguiendo las instrucciones de esta [guía]("http://www.guia-ubuntu.org/index.php/Xgl_y_Beryl").

Todo bien. No hubo ningún mensaje de error raro.
Pero reinicio X y entro en la sesión que teoricamente debería tener todas los chiches de Beryl, pero no se da por enterado. Nada de nada, una sesión comun  y corriente. Salvo que me pasó esto que dice [acá]("http://www.guia-ubuntu.org/index.php/Xgl_y_Beryl#Problema_con_la_decoraci.C3.B3n_de_ventanas_e_iconos"), nada de importancia, que se soluciona fácil.

Entonces mi pregunta es: se activa de alguna manera??? Por ahi tengo un menu en Sistema/Preferencia, pero en ningun lado dice "Activar Beryl"....

(estoy con Ubuntu Edgy Eft, AMD64)

---

### Post by divague on 2007-02-17
cuando inicies ubuntu cuando te pide tu nombre de usuario y password tienes que seleccionar como sesion xgl, cuando ya estes adentro de ubuntu, abres una terminal y corres beryl-manager

---

### Post by bichopro on 2007-02-17
ya te contestaron mas arriba.

en sesiones puedes colocarlo como programa que se abra cuando carges la sesion

te recomiendo que primero entres a una sesion normal de gnome y le des a beryl-manager, ami me funciona perfecto asi

---

### Post by felipelerena on 2007-02-17
Para que se abra siempre por defecto al principio tenes que ir a "sesiones" en el "centro de control" y agregarlo en "programas al inicio"

---

### Post by zspikes on 2007-02-18
aprovecho la ocasion para preguntar como hago para poner el escritorio 3D y todos esos efectos copados. Hay q bajar algun plug in? como se instala?

Por cierto, hubo uno q otro problema durante la instalacion, pero el programa abre sin problemas, debo preocuparme?

gracias!

---

### Post by felipelerena on 2007-02-18
> **zspikes said:**
> aprovecho la ocasion para preguntar como hago para poner el escritorio 3D y todos esos efectos copados. Hay q bajar algun plug in? como se instala?

Por cierto, hubo uno q otro problema durante la instalacion, pero el programa abre sin problemas, debo preocuparme?

gracias!

no, tenes que tocar la configuracion de beryl y activar los plugins pertinentes. eso lo haces yendo al beryl settings manager

que problema hubo durante la instalacion?

---

### Post by QUASAR_FREAK on 2007-02-18
Esas guias ke posteo matog explikan komo instalarlo, pero en xgl, te rekomiendo ke si tenes una plaka de video intel o nvidia uses aiglx y esta [guia]("http://quasarfreak.com.ar/wordpress/?page_id=4") y ke leas bastante antes de instalarlo porke es soft en beta.

La forma mas rapida para instalarlo es bajar Envy de la pagina de alberto milone, instalarlo y ejekutarlo desde modo texto (ctrl+alt+f1). (de esta forma tendremos la ultima version de los drivers de nvidia, ojo ke si luego aktualizamos el kernel vamos a tener ke llamar a envy otra vez)
Agregar los repositorios estables o svn de beryl o compiz a nuestra lista de repositorios, esto los sakamos de las paginas oficiales de cada window manager.

Y por ultimo instalamos:

En kaso de compiz:
sudo apt-get install compiz

En kaso de beryl:
sudo apt-get install beryl.

Paginas oficiales de kada uno:
Envy:
[http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)

Beryl:
[http://www.beryl-project.org/](http://www.beryl-project.org/)

Compiz:
[http://www.go-compiz.org/index.php?title=Main_Page](http://www.go-compiz.org/index.php?title=Main_Page)

---

### Post by zspikes on 2007-02-18
me acabo de mandar el pedo de mi vida jaja. quise instalar los drivers de la nvidia usando este tutorial:
[http://benux.wordpress.com/2006/10/08/aceleracion-grafica-nvidiaati/](http://benux.wordpress.com/2006/10/08/aceleracion-grafica-nvidiaati/)
y no se q carajo salio mal q cuando reinicie no andaba mas la interfaz grafica, asiq a reinstalar ubuntu jeje.

Me dijeron por ahi q me conviene bajarme el ubuntu 6.10 para usar la ultima version de beryl, asiq ando en eso, pero todavia no encuentro una forma facil de instalar beryl, grrrrr.
En fin, cuando tenga instalado el 6.10, intento de nuevo y les cuento como me fue

bytes!

---

### Post by cacharreo on 2007-02-18
Amigos la guia ideal para instalar Beryl es
[http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu](http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu) :guitar:

---

### Post by felipelerena on 2007-02-18
[zspikes]("http://ubuntuforums.org/member.php?u=240985") esto no es windows, no necesitas reinstalar todo el sistema cuando instalas mal un driver.

para la proxima:

cuando te pase eso tenes que cambiar el xorg.conf por el back up que te crearon los drivers de nvidia cuando los instalaste.
o siemplemente editar el xorg.conf y canviar lo que dice "nvidia" por "nv" en la seccion de la placa de video

---

### Post by zspikes on 2007-02-18
si, se q no es win gracias a dios jaja... pero entiendanme q hace muy poco migre y me estoy acostumbrando de a poco. Ya se q no hace falta instalar todo el sistema de nuevo, pero me venia bien porq toque mas de una cosa q no debia jeje. todo sea por aprender.

Sigo rabiando con el ******* beryl, si no es un kilombo es otro. ahora tengo problemas para agregar el universe y multiverse... hago todo lo q me dicen en [http://www.guia-ubuntu.org/index.php/Activar_universe_y_multiverse](http://www.guia-ubuntu.org/index.php/Activar_universe_y_multiverse) pero el ultimo archivo falla no se por q... no hay forma!

ACTUALIZACION:

Bien, continuando con mi desesperado intento por tener el maldito cubito, estoy siguiendo el tutorial de cacharreo: [http://wiki.beryl-project.org/wiki/I...eryl_on_Ubuntu](http://wiki.beryl-project.org/wiki/I...eryl_on_Ubuntu)
y nuevamente un problema similar al darle upgrade a los paquetes:

> Err [http://packages.freecontrib.org](http://packages.freecontrib.org) edgy Release.gpg
  Fallo la conexión
Ign [http://packages.freecontrib.org](http://packages.freecontrib.org) edgy Release
Ign [http://packages.freecontrib.org](http://packages.freecontrib.org) edgy/free Packages
99% [Esperando las cabeceras]



alguna idea? gracias!!!

---

### Post by QUASAR_FREAK on 2007-02-18
Instala esto [http://3v1n0.tuxfamily.org/pool/edgy/3v1n0/3v1n0-sources-list_0.3-3v1ubuntu0edgy1_i386.deb](http://3v1n0.tuxfamily.org/pool/edgy/3v1n0/3v1n0-sources-list_0.3-3v1ubuntu0edgy1_i386.deb)

Solo si tenes edgy.

Ahi tenes todos los repositorios de todo lo ke podes necesitar.
Si algun repo te jode simplemente desaktivalo, mientras no sea un ofician no pasa naranja.

---

### Post by Mafber on 2007-02-18
Hola. Hace unos días tuve que reinstalar los drivers de video y beryl. Yo seguí esta [guía]("http://wiki.beryl-project.org/index.php/Install/Ubuntu/Edgy/AiGLX") y me funcionó todo bien. Suerte

---

### Post by matog on 2007-02-19
Yo lo instale con XGL....para probar con XGL es mejor desinstalar todo lo que instale?

---

### Post by jpmorelli on 2007-02-19
Yo el beryl lo instalé siguiendo al pie de la letra esta guía, previamente usé ENVY para instalar el driver de mi placa nvidia

[http://wiki.beryl-project.org/index.php/Install/Ubuntu/Edgy/AiGLX]("http://wiki.beryl-project.org/index.php/Install/Ubuntu/Edgy/AiGLX")

También le agregué estas líneas porque no me salían los bordes y encontré las líneas mágicas.: 

append the following to your /etc/X11/xorg.conf in the “Device” section:

      Option         "AddARGBGLXVisuals" "True"
      Option         "RenderAccel" "True"
      Option         "AllowGLXWithComposite" "True"
      Option         "backingstore" "True"
      Option         "TripleBuffer" "True"

( lo de los bordes copiado de [http://nlindblad.org/author/admin/](http://nlindblad.org/author/admin/) )

---

### Post by zspikes on 2007-02-20
Perdon q insista tanto, pero no me termina de quedar clara la cosa. He seguido la mayoria de los tutoriales q encontre al pie de la letra y no logro resultados satisfactorios.
Por ahi leo cosas como edgy u otras y no tengo idea q es. Solo se q tengo ubuntu 6.06 q me regalo un amigo y una nvidia gforce 5200.

Q tutorial me conviene seguir? q precauciones debo tener?

Gracias y perdonen la ignorancia :(

PD: y si alguien se ofrece a agregarme al messenger para ayudarme un toke se lo agradeceria eternamente: gcibeira(arroba)gmail.com

---

### Post by zspikes on 2007-02-20
De nuevo yo... estoy muy enojado, estube investigando un poco y descubri q tengo  Ubuntu 6.06 (Dapper Drake) y leyendo en esta pagina [install beryl on ubuntu]("http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu#Ubuntu_6.06.x_.28Dapper_Drake.29") descubri q beryl no anda en esta version de ubuntu... grrrrrr
Probe bajar ubuntu 6.10 de shipit.ubuntu.com pero por algun extraño motivo la descarga termina al toke y el archivo queda dañado :S

alguna idea? gracias!

---

### Post by marianom on 2007-02-20
Que actualices directamente desde Dapper a Edgy con [este tutorial]("https://help.ubuntu.com/community/EdgyUpgrades").
Tené en cuenta que lleva su buen rato. Tené paciencia.

---

### Post by matog on 2007-02-20
> **matog said:**
> Yo lo instale con XGL....para probar con XGL es mejor desinstalar todo lo que instale?
Perdon, reescribo. Para probar con AIXGL, tengo que desinstalar todo lo que instalé antes?

---

### Post by felipelerena on 2007-02-20
AIXGL == AIGLX ?
supongo...
depende que hayas instalado, te recomiendo instalar automatix bleeder si o pudiste instalar ninguno de los tutoriales que hay dando vueltas por ahi

---

### Post by Mafber on 2007-02-20
Hola a todos!!! aprovecho a preguntar: beryl no funciona en Dapper??? la pag. que pasas Zspikes dice que sí (pero no estoy seguro). 
A modo de consejo: instalen beryl con cualquiera XGL o AIGLX. No se calienten tanto por ahora. 1º hagan que les funcione y después se preocupan, cuando la tengan más clara.. por esas siglas raras. :cool: 
A disfrutar!!!! :popcorn:

---

### Post by zspikes on 2007-02-21
SEÑORAS Y SEÑORES!!! ZSPIKES YA TIENE BERYL!!!!! :D gracias a la ayuda de todos ustedes!!!

ahora vamos con los problemas y las dudas jaja:
1-cuando abro una terminal me sale una ventana en blanco, no puedo escribir nada ni veo nada :S
2-las barras de las ventanas desaparecieron, esas donde esta el boton de cerrar, minimizar, etc...
3-como hago para poner una imagen de fondo al cubito y poner una arriba y abajo del mismo y todo eso?
4-donde se activan los efectos de transparencia y todo eso?

mil gracias nuevamente a todos!!! son unos capos! bytes!

---

### Post by BlackHero on 2007-02-21
jejee estaba leyendo lo de las barras en las ventanas lee mas atras que te postearon las lineas de como solucionarlo lo otro ni idea por que no tengo beryl xD

---

### Post by zspikes on 2007-02-21
si, lei lo de los bordes, edite el archivo y le agregue las lineas y nada, siguen sin aparecer los bordes.
Estube buscando por ahi como arreglarlo y encontre una q otra linea para agregar, pero sin resultados :S
Y ya q estamos les agrego un problemita... como cambio el tema con Emerald? abro el gestor y tengo todos los temas, pero no veo ningun boton q diga cambiar de tema o algo, y le hago clicks hasta decir basta y no pasa nada jeje.

Muchas gracias y tenganme paciencia por favor jaja, bytes!

---

### Post by Mafber on 2007-02-21
Hola!!!! Zspikes tuve el mismo problema que vos y lo arreglé (si arreglo jajaja) cuando puse esa en la sección "screen" :
Option "AddARGBGLXVisuals" "True"
Option “DisableGLXRootClipping” “True”

Otra cosa que podría llegar a hacer es que el tema que tengas puesto con "emerald" sea sin barras.

Estamos todos para ayudarnos entre todos!!! :)  
( yo tambien soy nuevo en el universo Linux :lol: )

---

### Post by zspikes on 2007-02-21
ok, ahi puse las lineas q me dijiste en screen, enseguida reinicio y comento q tal me fue. Pero no entendi la parte de emerald, sin barras? Solo quiero saber como se usa, como cambio un tema.
Gracias!

---

### Post by Mafber on 2007-02-21
mira, el "emerald" te permite elejir como queres que se vean las barras (tamaño, colores, etc) fijate en el icono que te sale de Beryl que si haces boton derecho en la parte de arriba del menú que te sale hay dos opciones:
1º La de mas arriba es para configural a beryl .Que si vas a desktop te salen las opciones para verlo como cubo. (adentro de ver como cubo, en el panel derecho, vas a ver varias solapas, una es para hacerlo transpoarte) Perdón que no te de una idea clara, pero es que estoy en windows y no puedo cambiar por ahora.
2º es "emerald": desde ahi podes configurar como queres que se vean las barras.
Suerte!!!!!

Dentro de un raro entro a linux y si que voy a poder ayudar mejor :guitar:

Una cosa más que se me pasó.... cada vez que inicio beryl las ventanas se me salen de la pantalla pero solo la parte de la barra (cerrar, minimizar, etc) lo que tengo que hacer en maximizarlas desde la barra de tareas.

---

### Post by zspikes on 2007-02-21
no se q paso con la linea q me pasaste, reinicie y no arrancaba la interfaz grafica, asiq tube q reeditar el archivo y borrar las lineas :S
Lo de emerald si se como entrar en la configuracion, hago click derecho en el icono de beryl y entro en el gestor de temas de emerald. Pero lo q no se como hacer es cambiar al tema q elija. Por ej, hay un tema en el gestor q se llama red crystal o algo asi, y quiero poner ese y no se como.

---

### Post by Mafber on 2007-02-21
solo le das click y cambia todo el entorno. proba con elejir otro y con solo darle click vas a ver que cambia todo el decorado (no es necesario tocar ningun boton que diga "aceptar")
tenes otros temas??? porque si no los tenes vas a tener que instalarlos (creo que es así) 
sudo apt-get install emerald-themes
che con respecto a poner las lines en el xorg.conf: si solo pones esta en screen?
Option "AddARGBGLXVisuals" "True"

---

### Post by zspikes on 2007-02-21
ahi agregue la linea y sigue sin resultados. Supongo q no puedo cambiar el tema porq no se ven los bordes, ya no se q probar, nada da resultado :S

Edit: me acabo de dar cuenta q por lo menos me soluciono el problema de la consola :D ya es algo jeje

---

### Post by Mafber on 2007-02-21
aguanta un rato que deben de llegar los pibes que la tienen muchisimooooo mas clara que yo. Que no decaiga el ánimo!!!! por lo menos tenes el cubo.. jajaja
Hay un plugin que me trajo muchos problemas antes de que salga la vesion 0.2 de beryl que es el de "jpg" y con la version 0.2 se me cierra si pongo distintos fondos de pantalla en los lados del cubo.
Bueno... Suerte... ya te van a responder!!!! :guitar: y dentro de poco vas a ver que te va a funcionar todo de 10!!!

---

### Post by zspikes on 2007-02-21
muchas gracias por la buena onda compadre, por lo menos solucionamos lo de la consola jaja. Dejo la duda planteada a ver quien me ayuda :P

No puedo activar los bordes de las ventanas, esa barrita donde va el titulo del programa y los botones de cerrar, minimizar, etc... y creo q por eso no puedo cambiar el tema de emerald, a ver quien me da una manito?

Gracias de antemano!

---

### Post by zspikes on 2007-02-21
no me la van a creer :( me dijeron q actualizando beryl a la ultima version se solucionaba ese tema, entonces no se me ocurrio otra q actualizarlo, y ahora no me anda :S
pruebo abrirlo y atina a cambiar, pero al final queda el gnome comun nomas, como puedo hacer?

probe desinstalarlo y volver a instalarlo como yo sabia, pero sin resultados :S alguna idea? gracias!

PD: les pego el error q me tira en la consola

>  **************************************************************
* Beryl system compatibility check                           *
**************************************************************

Detected xserver                                : NVIDIA

Checking Display :0.0 ...

Checking for XComposite extension               : passed (v0.3)
Checking for XDamage extension                  : passed
Checking for RandR extension                    : passed
Checking for XSync extension                    : passed

Checking Screen 0 ...

Checking for GLX_SGIX_fbconfig                  : passed
Checking for GLX_EXT_texture_from_pixmap        : passed
Checking for non power of two texture support   : passed
Checking maximum texture size                   : passed (4096x4096)

[Warning ]: Relaunching beryl with __GL_YIELD="NOTHING"

**************************************************************
* Beryl system compatibility check                           *
**************************************************************

Detected xserver                                : NVIDIA

Checking Display :0.0 ...

Checking for XComposite extension               : passed (v0.3)
Checking for XDamage extension                  : passed
Checking for RandR extension                    : passed
Checking for XSync extension                    : passed

Checking Screen 0 ...

Checking for GLX_SGIX_fbconfig                  : passed
Checking for GLX_EXT_texture_from_pixmap        : passed
Checking for non power of two texture support   : passed
Checking maximum texture size                   : passed (4096x4096)

beryl: symbol lookup error: /usr/lib/beryl/libjpeg.so: undefined symbol: jpeg_std_error


---

### Post by BlackHero on 2007-02-21
zspickes que se siente por lo menos tener el cubito es lindo? se siente bien? te sentis adentro de algo? o es como tener algo nose re flash nunca antes visto en las compus que lindo debe ser el cubito =(

---

### Post by Mafber on 2007-02-21
Hola de nuevo. no se si esto puede mejorarte la situación. despues de desintalarlo borra la carpeta que esta en tu directorio personal ".Beryl" fijate que tiene un punto adelante, lo que quiere decir que esta oculto.
Suerte!!!!!

---

### Post by zspikes on 2007-02-22
Ya lo solucione, no se como pero esta andando de nuevo jaja. La verdad q si, se siente hermoso tener el cubito, sobretodo para decirle a los giles q nombran el vista "mira mamon, el mio es mas bonito y no chupa todos los recursos!!!"... "ademas es gratis!!! hoho" jeje.

Gente, disculpen por haber roto tanto los quinotos, no me gusta preguntar tanto, pero soy demasiado nuevo en esto y es hasta q le agarre un poquito la mano. Gracias a todos por el aguante y la buena onda!!! ;)

bytes!!!

---

### Post by matog on 2007-03-13
No tengo forma de ver el cubo. Andan algunos efectos...pero el cubo???
Ah, y no me deja cambiar de escritorio...
(estoy con edgy amd64)

---

### Post by jajajavi on 2007-03-15
a ver si te sirve, yo tenía el beryl a medio instalar (no andaba) y encontré estas líneas en un tutorial de ubuntu edgy para macbook que funcionaron tanto en la mac como en la pc amd64:

```
sudo sed -i '$adeb http://ubuntu.beryl-project.org/ edgy main' /etc/apt/sources.list
wget http://ubuntu.beryl-project.org/root@lupine.me.uk.gpg -O- | sudo apt-key add -
sudo apt-get update
sudo apt-get -y install beryl emerald-themes
beryl-manager
```

---

