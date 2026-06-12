---
title: "[HOW-TO] Compiz Fusion en Ubuntu"
date: 2007-06-23
forum: Argentina Team
---

### Post by sdm_cacto on 2007-06-23
ADVERTENCIA: Hacer esto bajo tu propio riesgo

Antes de todo tenes q instalar los drivers de tu placa de video, ésto se puede hacer facilmente gracias a un prgramita llamado [Envy]("http://albertomilone.com/nvidia_scripts1.html")

----------------------------------------------------------------------------

(Para ATI se debe realizar un paso mas...leer el final del Post)

Primero eliminar Compiz y Desktop Effects

> 
sudo apt-get remove compiz-core desktop-effects

Updatear:
> 
sudo aptitude update

Añadir los repos Compiz-git y Compiz Fusion git, administrados por Treviño: agregar lo siguiente a tu /etc/apt/sources.list

> # Treviño's Ubuntu feisty EyeCandy Repository (GPG key: 81836EBF - DD800CD9)
# Many eyecandy 3D apps like Beryl, Compiz, Fusion and kiba-dock snapshots
# built using latest available (working) sources from git/svn/cvs... 
deb [http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb) feisty eyecandy 
deb-src [http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb) feisty eyecandy


Paquetes en: [http://3v1n0.tuxfamily.org/dists/feisty/eyecandy/](http://3v1n0.tuxfamily.org/dists/feisty/eyecandy/)

Agregar Keys
> 
KEY=81836EBF; gpg --keyserver subkeys.pgp.net --recv $KEY && gpg --export --armor $KEY | sudo apt-key add -

Updatear

> sudo aptitude update

Para instalar Compiz:

> sudo apt-get install compiz  # compiz-gnome 

Y/O

compiz-kde (si usas Kubuntu)
Para instalar CompizConfig:
> 
sudo apt-get install compizconfig-settings-manager
sudo apt-get install libcompizconfig-backend-gconf

Y/O (si usas Kubuntu)
sudo apt-get install libcompizconfig-backend-kconfig

Para instalar Compiz Fusion Plugins

>  sudo apt-get install compiz-fusion-*
Para correr Compiz Fusion
apreta alt+F2 y escribi

> compiz --replace

Para configurar Compiz Fusion ir a  Sistema>Preferencias>CompizConfig Settings Manager

------------------------------------------------------------------------

Para placas ATI Compiz Fusion debe correr sobre XGL:
> 
sudo apt-get install xserver-xgl

Escribimos un script para poder iniciar XGL

> sudo gedit /usr/local/bin/startxgl.sh

Dentro del archivo escribir esto y luego guardar:

> #!/bin/sh
Xgl :1 -fullscreen -ac -accel xv:pbuffer -accel glx:pbuffer &
DISPLAY=:1
exec dbus-launch --exit-with-session gnome-session

Hacer el script ejecutable:

> sudo chmod a+x /usr/local/bin/startxgl.sh

Ahora, agregar la opcion para iniciar XGL en el menu GDM: 

> sudo gedit /usr/share/xsessions/xgl.desktop

Dentro del archivo escribir esto y luego guardar:
> 
[Desktop Entry]
Encoding=UTF-8
Name=GNOME + XGL
Comment=
Exec=/usr/local/bin/startxgl.sh
Icon=
Type=Application

Hacer el script ejecutable:
> 
sudo chmod a+x /usr/share/xsessions/xgl.desktop

Luego reiniciar (o apretar CTRL+ALT+BACKSPACE) e iniciar la secion Gnome con XGL, abrir una terminal y escribir
>  compiz --replace

---

### Post by zspikes on 2007-06-23
casi rompo todo :S cuando ponia "sudo apt-get install compiz # compiz-gnome " me tiraba un error q no recuerdo bien... no le di pelota y segui los pasos, y todos me tiraron error. Al final anduvo, pero sin bordes de ventanas, no se podia rotar el cubo ni nada, y no podia acceder a las opciones.

Lo peor de todo es q saque beryl para probarlo, y me costo reinstalarlo... por suerte safe esta vez. Ahora voy a probar de nuevo y pego el error q me tiro. saludos!

EDIT:

aqui esta el error del que hablaba:

> gera@ameli:~$ sudo apt-get install compiz # compiz-gnome
Leyendo lista de paquetes... Hecho
Creando árbol de dependencias       
Leyendo información de estado... Hecho
compiz ya está en su versión más reciente.
Tal vez quiera ejecutar `apt-get -f install' para corregirlo:
Los siguientes paquetes tienen dependencias incumplidas:
  compiz: Depende: compiz-decorator
  compiz-gnome: Depende: compiz-gtk (= 1:0.3.6-1ubuntu13) pero no va a instalarse
E: Dependencias incumplidas. Intente 'apt-get -f install' sin paquetes (o especifique una solución).


espero sus respuestas :)

---

### Post by sdm_cacto on 2007-06-23
Jaja, ahroa agregue una advertencia arriba... esta guia la saque de un sticky en este mismo foro.

Hace ésto, instala emerald; apretá alt+F2 y pone
> compiz --replace -c emerald &

teniendo instalado emerald por supuesto.
Fijate en Synaptic si t falta agregar algo importante de los paquetes git  buscando "Compiz"

[Éste]("http://ubuntuforums.org/showthread.php?t=481314") es el thread original


EDIT:probaste hacer lo q t dice el mismo error? osea hace "sudo apt-get -f install" a ver si t instala las dependencias incumplidas

---

### Post by zspikes on 2007-06-23
no se que **** me mande... no puedo instalar nada :S el synaptic dice q hay paquetes rotos
y por consola me sigue tirando el mismo error... no se q pasa, grrrrrr

---

### Post by undiaperfecto on 2007-06-23
Yo lo probe en un ubuntu recien instalado de un amigo, y no hubo manera, me tiro los mismos errores que marcan mas arriba, asi que voy a esperar un tiempo para testearlo.

---

### Post by zspikes on 2007-06-23
yo tambien me parece q voy a esperar a q salga una version un poco mas estable, o por lo menos, mas instalable XD
igual, muchas gracias por el dato!!! :D

---

### Post by spg76 on 2007-06-24
Yo lo instalé ayer y por suerte todo fue bien (tengo una placa Intel integrada). La verdad que está buenisimo, sobre todo el efecto "Expo".
Funciona bastante bien, pero encontré un par de problemas como que los "window previews" no los hace minimizados, el efecto "ventanas gelatinosas" es malisimo comparado con Beryl, y reproducir video con mplayer es una tortura. Así y todo, me sorprendió con la fluidez que funciona.
Según mi experiencia, la instalación vale la pena si queres probarlo porque no es muy confiable a nivel estabilidad como para usarlo en el día a día.
Por ahora seguiré con Beryl hasta que haya una versión más estable.

---

### Post by sdm_cacto on 2007-06-24
Corregí la parte de compizconfig


> sudo apt-get install compizconfig-settings-manager
sudo apt-get install libcompizconfig-backend-gconf

AND/OR (If you use Kubuntu)
sudo apt-get install libcompizconfig-backend-kconfig

---

### Post by damcito on 2007-06-24
como puedo hacer que compiz --replace se auto ejecute en el inicio de mi KDE?

---

### Post by zspikes on 2007-06-24
grrrrr, no hay forma... me sigue rompiendo las pelotas con
> E: Dependencias incumplidas. Intente 'apt-get -f install' sin paquetes (o especifique una solución).


alguien sabe q ****** es esto y como se soluciona? gracias!

---

### Post by Al_maverick on 2007-06-24
tenes un problema en el apt-get. Tenes que correr ese comando que dice antes q puedas seguir utilizandolo.
O sea, pone:

sudo apt-get -f install

Y eso deberia solucionarte el problema, despues podes seguir probando.

---

### Post by KAYAMAN0 on 2007-06-24
Muchas gracias por la respuesta.
Voy a probar eso.

saludos

---

### Post by zspikes on 2007-06-26
> **Al_maverick said:**
> tenes un problema en el apt-get. Tenes que correr ese comando que dice antes q puedas seguir utilizandolo.
O sea, pone:

sudo apt-get -f install

Y eso deberia solucionarte el problema, despues podes seguir probando.

Definitivamente el "apt-get" me anda para el ***, la verdad q no se como arreglarlo :(
corri el comando q me dijiste, y me tira este error:
```
Se encontraron errores al procesar:
 /var/cache/apt/archives/compiz-gnome_1%3a0.5.1+git20070626~3v1ubuntu0_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

alguien me puede decir como lo soluciono por favor? gracias!

---

### Post by Al_maverick on 2007-06-27
> **zspikes said:**
> Definitivamente el "apt-get" me anda para el ***, la verdad q no se como arreglarlo :(
corri el comando q me dijiste, y me tira este error:
```
Se encontraron errores al procesar:
 /var/cache/apt/archives/compiz-gnome_1%3a0.5.1+git20070626~3v1ubuntu0_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

alguien me puede decir como lo soluciono por favor? gracias!

pone:

sudo dpkg -C

y fijate que te tira. Eso postealo en un thread aparte para poder seguirlo mejor y no salirnos de tema en esta thread.

---

### Post by zspikes on 2007-06-27
no me van a creer lo q me paso! exploto todo jaja, rompi todo, asiq formatee :P si si, no me reten... solucion windowsera, pero ya era hora, pobre maquina, estaba muy molida a palos jeje.
Asiq ya estoy con un sistema limpito, y ya le puse compiz fusion siguiendo [esta]("http://www.compiz.org/Compiz_and_Copmiz_Fusion_GIT_Ubuntu_Repository") guia.
Se lo ve re piola :D ya le voy a ir agarrando la mano a ver q onda, aunq me sigue pareciendo mas comodo beryl.

saludos!!! y gracias por todo!

---

### Post by clasificado on 2007-06-28
> exploto todo jaja, rompi todo, asiq formatee :P

¡¡¡Buuuuu!!!!

Clasificado

---

### Post by anaspeople on 2007-06-28
Yo tenía ese problema y lo solucioné desinstalando todo lo relacionado con compiz desde synaptic, aún cuando te dice que quitará ubuntu-desktop. Luego seguí el tutorial y sin problemas.
Bueno dos problemas. 
1. Solo me arranca con sudo compiz -- replace
2. No consigo cambiar el theme de emerald ni añadir más efectos.... desde ccsm
(compiz config settings manager) todo con sudo por supuesto....

Alguna sugerencia?

---

### Post by quaid on 2007-06-28
Resumiendo instale todo y no anda ni para atras , algo carga pero no tengo el cubo ni nada, algo me falta,
extraño beryl!

Resumiendo, instalo compiz, compiz fusion... y despues? de ventanas que se usa? emerald, compcomm? teoricamente decorador de ventanas deberia de funcionar con el mismo metacity de gnome no?

el replace --c me recarga la pantalla pero no hay cubo ni nada , alguna idea?

---

### Post by Al_maverick on 2007-06-28
no se el fusion, pero el compiz comun usa el gnome-window-decorator
creo q tambien hay una opcion para usarlo con metacity

---

### Post by spg76 on 2007-06-28
Fusion puede usar gnome-window-decorator (si alguno tiene instalado Beryl, verá que en la sección "decorador de ventanas" aparece como "Decorador de ventanas GTK") o sino Emerald.
Para los que tengan problemas iniciando Fusion, es importante no estar usando Beryl cuando ponen "compiz --replace" porque esto genera algunos problemas en la carga.
Si lo estan usando, pasen a "Metacity" y después pongan "compiz --replace".

---

### Post by quaid on 2007-06-29
Esto me esta cansando de sobre manera
```
quaid@avion:~$ compiz --replace -c emerald &[1] 9178
quaid@avion:~$ grep: /proc//smaps: No existe el fichero ó directorio
Adding core settings (General Options)
Adding plugin annotate (annotate)
Adding plugin blur (blur)
Adding plugin clone (clone)
Adding plugin cube (cube)
Adding plugin dbus (dbus)
Adding plugin decoration (decoration)
Adding plugin fade (fade)
Adding plugin fs (fs)
Adding plugin glib (glib)
Adding plugin inotify (inotify)
Adding plugin minimize (minimize)
Adding plugin move (move)
Adding plugin place (place)
Adding plugin plane (plane)
Adding plugin png (png)
Adding plugin regex (regex)
Adding plugin resize (resize)
Adding plugin rotate (rotate)
Adding plugin scale (scale)
Adding plugin screenshot (screenshot)
Adding plugin svg (svg)
Adding plugin switcher (switcher)
Adding plugin video (video)
Adding plugin water (water)
Adding plugin wobbly (wobbly)
Adding plugin zoom (zoom)
Adding plugin animation (animation)
Adding plugin expo (expo)
Adding plugin imgjpeg (imgjpeg)
Adding plugin neg (neg)
Adding plugin opacify (opacify)
Adding plugin put (put)
Adding plugin resizeinfo (resizeinfo)
Adding plugin ring (ring)
Adding plugin scaleaddon (scaleaddon)
Adding plugin snap (snap)
Adding plugin text (text)
Adding plugin thumbnail (thumbnail)
Adding plugin vpswitch (vpswitch)
Adding plugin wall (wall)
Adding plugin winrules (winrules)
Adding plugin addhelper (addhelper)
Adding plugin bench (bench)
Adding plugin crashhandler (crashhandler)
Adding plugin cubereflex (cubereflex)
Adding plugin extrawm (extrawm)
Adding plugin fadedesktop (fadedesktop)
Adding plugin firepaint (firepaint)
Adding plugin group (group)
Adding plugin mblur (mblur)
Adding plugin reflex (reflex)
Adding plugin showdesktop (showdesktop)
Adding plugin splash (splash)
Adding plugin trailfocus (trailfocus)
Adding plugin fakeargb (fakeargb)
Adding plugin snow (snow)
Adding plugin tile (tile)
Backend     : ini
Integration : true
Profile     : default
Initializing core options...done
Initializing decoration options...done
/usr/bin/compiz: line 671:  9260 Fallo de segmentación  (core dumped) $*

```

q ****** le pasa? y disculpen el vocabulario pero me tiene podrido esto hace 3 dias q lo instalo y lo desinstalo y todo el mundo te manda el magico alt+F2 y replace que no sirve para nada

Alguna idea?

---

### Post by Al_maverick on 2007-06-29
en mi caso, yo tengo q iniciar el compiz de esta manera. No me acuerdo bien ahora por que era, pero si no, me da un error.

LIBGL_ALWAYS_INDIRECT=1 compiz --replace &

Y tranquilo. Ya probaste fijarte en el foro de compiz si alguien tuvo un error parecido?

---

