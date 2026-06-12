---
title: "Problema con Gnome"
date: 2007-07-27
forum: Argentina Team
---

### Post by sdm_cacto on 2007-07-27
[FONT="Tahoma"][FONT="Trebuchet MS"]OK, esto es asi:
Cuando ingreso a mi sesion de Gnome, o Gnome con XGL carga un poco y luego se cuelga, es decir, no me carga el wallpaper, solo la barra de tareas y no me deja acceder al menu de Gnome, el mouse anda lento tambien, com osi cargara algo pero no puede ejecutar el Monitor de Sistema tampoco, aunque puedo girar el cubo de Compiz Fusion.

Esto no es asi cuando entro en recovery mode, tampoco me pasa con Enlightenment por lo que deduzco que debe ocurrir al cargar algun servicio, los que no puedo desactivar, porq en recovery mode simplemente no me lo permite.

Alguien tiene idea de que puede pasar, o como puedo desactivar los servicios para ir habilitandolos uno por uno (y asi saber cual falla)??

O sino aunque sea encontrar el log de Gnome  que me ayude un poco

Espero haber sido claro, gracias[/FONT][/FONT]

uso Ubuntu Feisty

---

### Post by MeduZa on 2007-07-27
> **sdm_cacto said:**
> [FONT="Tahoma"][FONT="Trebuchet MS"]OK, esto es asi:
Cuando ingreso a mi sesion de Gnome, o Gnome con XGL carga un poco y luego se cuelga, es decir, no me carga el wallpaper, solo la barra de tareas y no me deja acceder al menu de Gnome, el mouse anda lento tambien, com osi cargara algo pero no puede ejecutar el Monitor de Sistema tampoco, aunque puedo girar el cubo de Compiz Fusion.

Esto no es asi cuando entro en recovery mode, tampoco me pasa con Enlightenment por lo que deduzco que debe ocurrir al cargar algun servicio, los que no puedo desactivar, porq en recovery mode simplemente no me lo permite.

Alguien tiene idea de que puede pasar, o como puedo desactivar los servicios para ir habilitandolos uno por uno (y asi saber cual falla)??

O sino aunque sea encontrar el log de Gnome  que me ayude un poco

Espero haber sido claro, gracias[/FONT][/FONT]

uso Ubuntu Feisty

Hola
**Creo** que eso son los drivers de nvidia que se enloquesieron pasa normalmente despues de un update de kernel o cosas asi.
proba instalarlos de nuevo (los ultimos) con sh aca_nombre_del_driver.bin desde modo texto

si no tenes nvidia busca como se hace con la tuya

si no es eso ni idea

---

### Post by sdm_cacto on 2007-07-27
OK medu, tengo ati pero voy a desinstalar los drivers igual.
sino pruebo cambiando el kernel.
luego informo, gracias por contestar


EDIT: bueno, no es problema de drivers

Cuando entro por enlightenment y abro programas GTK empieza a andar lento, por lo q debe ser problema de GTK, tampoco del kernel

---

### Post by sdm_cacto on 2007-07-28
Vamos muchachos necesito ayuda!

---

### Post by mpbe on 2007-07-28
Proba entrar como root. Anda a tu carpeta personal, mostra los archivos ocultos y borra (o cambia el nombre) las carpetas .gconf, .gnome, .gnome2 y cualquier otra que te parezca sea de configuracion de gnome.
Si el problema es de configuracion de gnome, asi vas a entrar pero perdes toda la configuracion. Una vez que funcione podes probar recuperar las carpetas de a una para ver cual es la que te ****.


Saludos

---

### Post by kowal on 2007-07-28
O probá con otro usuario.

---

### Post by sdm_cacto on 2007-08-01
OK, borre todas las carpetas de mi usuario y no se solucionó, me quedaria entrar como root o crear otro usuario pero no tengo ni idea de como hacerlo con Enlightenment o desde la Terminal.

La verdad es q me tiene bastante harto E17 , pero me viene salvando las papas y es livianito jaja

---

### Post by kowal on 2007-08-01
Para crear otro usuario:

```
sudo adduser <usuario>
```

---

### Post by sdm_cacto on 2007-08-01
Bueno, cree otro usuario y tengo el mismo problema, tambin probe cambiando el kernel y nada.

Me faltaria probar ocmo usuario root (q no se como) pero yo creo q es un problema de GTK.

Reinstalaría, pero la idea de todo ésto es aprender que pasa, no tiene sentido reinstalar en un SO que no se degrada con el paso del tiempo.

---

### Post by jpmorelli on 2007-08-01
Y que pasa si antes de reinstalar no te haces un 

sudo apt-get install ubuntu-desktop

o probá

sudo apt-get -f install

sudo dpkg --configure -a

como para ver si no tenes dependencias rotas o a medio instalar...
:confused:

---

### Post by yogo on 2007-08-01
Problemente es una problema con gtk ...tenia lo mismo problema con una tema/carpeta el systema no pudo encontrar.  En me caso Desktop Effects fui necessario para cambiar las settings.

---

### Post by sdm_cacto on 2007-08-04
Bueno, no se preocupen mas... la semana q viene me llega una Geforce 6800 (me libro de mi ****** ATI y voy  a aprovechar para formatear)

---

