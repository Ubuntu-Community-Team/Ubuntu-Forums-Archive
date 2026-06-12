---
title: "Problema con Deluge-Torrent"
date: 2007-12-27
forum: Argentina Team
---

### Post by lega on 2007-12-27
Hola, bueno mi problema es el siguiente y lo cause yo, resulta que no tuve mejor idea que bajar un torrent de distintos trackers, es decir, yo tenia completado un torrent de un tracker y para subir el ratio de otro tracker no tuve mejor idea q ponerlo a bajar , de manera que al estar completo,solo lo subiria y ganaría en ratio, entonces me quedo el mismo archivo dos veces (completo)en la lista de descargas.
Deluge me lanzo una advertencia de torrents duplicados que yo por supuesto no hice caso ](*,) al otro dia al encender la pc y querer iniciar el programa no arranca.
por consola me tira lo siguiente 
checking for ubuntu...
found and fixing ubuntu
checking for ubuntu...
found and fixing ubuntu
no existing Deluge session
Starting new Deluge session...
deluge_core; using libtorrent 0.13.0.0. Compiled with NDEBUG.
Applying preferences
Raising error: libtorrent reports this is a duplicate torrent
Traceback (most recent call last):
  File "/usr/bin/deluge", line 146, in <module>
    start_deluge()
  File "/usr/bin/deluge", line 127, in start_deluge
    interface = deluge.interface.DelugeGTK()
  File "/var/lib/python-support/python2.5/deluge/interface.py", line 54, in __init__
    common.CONFIG_DIR)
  File "/var/lib/python-support/python2.5/deluge/core.py", line 276, in __init__
    self.sync(True)
  File "/var/lib/python-support/python2.5/deluge/core.py", line 886, in sync
    raise e
deluge.core.DuplicateTorrentError: 'libtorrent reports this is a duplicate torrent'


probe instalando y volviendo a instalar y el error sigue,incluso borrando el archivo descargado y sigue, alguien tiene idea que puedo hacer?

Gracias por la ayuda

---

### Post by marianom on 2007-12-27
Que manera tan elegante de manejar un error que tienen estos muchachos... 
Antes que todo, es importante que puedas reportar esto con ellos así buscan una forma de dar mejores mensajes de error y/o algun fix para que funcione bien el programa.
Yendo ahora a tu problema, Deluge guarda info de sus configuraciones internamante así que por más que borres el torrent no va a pasar nada. Ahora no tengo Deluge instalado más así que no sabría decirte donde está :) (hace un sudo updatedb y un slocate "archivo" para donde guarda la copia) o reinstalalo pero esta vez corré un --purge para que elimine los archivos de configuracion existentes.

---

### Post by lega on 2007-12-27
Se me ocurrio mirar en los foros de Deluge y en las FAQS y ahi estaba la solucion
:) **"`rm ~/.config/deluge/persistent.state`**" borre ese archivo y arranco,
Gracias

---

### Post by Thalskarth on 2007-12-27
> **marianom said:**
> Que manera tan elegante de manejar un error que tienen estos muchachos... 

En si, es el sistema asi. Siempre que el Deluge tiene un fallo, se cierra solo. Y si era algo grave, deja de arrancar :P

yame cure de espanto con el, ahora se como domarlo XDDDDD

---

