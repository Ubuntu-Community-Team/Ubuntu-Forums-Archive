---
title: "Amarok no inicia"
date: 2007-02-07
forum: Argentina Team
---

### Post by spg76 on 2007-02-07
Como dice el título, amarok no inicia.
En la terminal me sale lo siguiente:
```
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
kdecore (KAction): WARNING: KAction::insertKAccel( kaccel = 0x8096190 ): KAccel object already contains an action name "play_pause"
QLayout "unnamed" added to QVBox "unnamed", which already has a layout
kdecore (KAction): WARNING: KAction::insertKAccel( kaccel = 0x8096190 ): KAccel object already contains an action name "play_pause"
QLayout: Adding KToolBar/mainToolBar (child of QVBox/unnamed) to layout for PlaylistWindow/PlaylistWindow
Amarok is crashing...
Running: gdb --nw -n --batch -x /tmp/kde-seba/amarokJyIi1a.tmp amarokapp 1941
Running: file `which amarokapp`
1.4.5 [___stripped][validity: 0.43][frames:  58][xine]

Amarok has crashed! We are terribly sorry about this :(

But, all is not lost! Perhaps an upgrade is already available which fixes the problem. Please check your distribution's software repository.

```

Ya probé reinstalando e incluso hoy actualicé a la versión 1.4.5 y no se arreglo.
¿Alguien tiene idea de como puedo arreglarlo?
Muchas gracias.

---

### Post by bichopro on 2007-02-07
desinstala, ve a tu carpeta home, ver archivos ocultos, borra la carpeta .amarok reinstala y prueba...quizas y solo quizas funcione

---

### Post by spg76 on 2007-02-07
> **bichopro said:**
> desinstala, ve a tu carpeta home, ver archivos ocultos, borra la carpeta .amarok reinstala y prueba...quizas y solo quizas funcione

Ya lo intente y nada. Igual no tengo la carpeta .amarok en mi home. La carpeta de configuración está en .kde/share/apps/amarok.

---

### Post by kowal on 2007-02-08
Probaste logueado como otro usuario?

---

### Post by screening on 2007-02-08
Actualizaste todo desde el gestor de actualizaciones?

"But, all is not lost! Perhaps an upgrade is already available which fixes the problem. Please check your distribution's software repository"

---

### Post by spg76 on 2007-02-08
> **kowal said:**
> Probaste logueado como otro usuario?
No, no probé. Voy a intentar cuando llegué a mi casa.

> **screening said:**
> Actualizaste todo desde el gestor de actualizaciones?

"But, all is not lost! Perhaps an upgrade is already available which fixes the problem. Please check your distribution's software repository"

Si, actualicé desde Synaptic. Esa aclaración me aparecía también en la versión 1.4.4, así que actualizarme no me arreglo el problema.

---

### Post by spg76 on 2007-02-08
Probé lo que me dijo kowal.
En lugar de crear otro usuario intenté correr el programa como root y funciona perfecto.
Me creó la colección, escuché unas canciones, corrí el script de letras; todo perfecto.
Entonces busqué en mi home algún archivo de configuración de Amarok y encontré uno llamado amaroksrc en '.kde/share/config'. Lo borré e inicie Amarok. Me apareció el asistente de inicio y una vez completado procedió a cargar el programa.
Si bien ahora inicia, no puedo hacer absolutamente nada porque después de unos segundos se cierra.
Si intentó correr el programa me pasa lo mismo; inicia, se queda pensando unos segundos y se cierra.
¿Alguna idea?

---

### Post by kowal on 2007-02-09
Si funciona bien con otro usuario, entonces es un problema de configuración. 

Probá desinstalando amarok (sudo aptitude purge amarok)
Y borrando todos los archivos/directorios de configuración de Amarok..

Yo encontré estos:

/etc/kde3/amarokrc
~/.kde/share/apps/amarok/*
~/.kde/share/config/amarokrc
/usr/share/apps/amarok/*
/usr/share/apps/profiles/amarok.profile.xml
/usr/share/config.kcfg/amarok.kcfg

Después volvé a instalar a ver que pasa.

Saludos

---

### Post by spg76 on 2007-02-09
kowal, hice todo lo que dijiste y sigo igual.
Lanzó el programa, inicia, se queda unos segundos y se cierra.
La salida de la terminal es la practicamente la misma que la del primer mensaje.
Voy a seguir investigando, si alguien se le ocurre algo, le estaré agradecido.
Saludos.

---

