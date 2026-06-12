---
title: "[SOLVED] Error de APT / APTITUDE"
date: 2007-11-24
forum: Argentina Team
---

### Post by User21 on 2007-11-24
Obtengo lo siguiente al querer instalar via apt / aptitude:

```
user21@DarkSide:~$ sudo aptitude install virtualbox
Leyendo lista de paquetes... ¡Error!
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/ar.archive.ubuntu.com_ubuntu_dists_gutsy_universe_binary-i386_Packages
E: No se pudo abrir o interpretar las listas de paquetes o el fichero de estado.
Leyendo lista de paquetes... ¡Error! 
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/ar.archive.ubuntu.com_ubuntu_dists_gutsy_universe_binary-i386_Packages
E: No se pudo abrir o interpretar las listas de paquetes o el fichero de estado.

```

y en Synaptic obtengo un dialogo con este mensaje: 

> No se ha podido inicializar la información de los paquetes

Ha ocurrido un problema imposible de corregir cuando se inicializaba la información de los paquetes.

Por favor, informe de ésto como un fallo en el paquete «update-manager» e incluya el siguiente mensaje de error:

'E:Encountered a section with no Package: header, E:Problem with MergeList /var/lib/apt/lists/ar.archive.ubuntu.com_ubuntu_dists_gutsy_universe_binary-i386_Packages, E:No se pudieron analizar o abrir las listas de paquetes o el archivo de estado.'

Alguna idea ? He visto algunos posts similares , sustituyendo dpkg/status por status-old, pero no hay caso.

...

---

### Post by gepatino on 2007-11-24
probaste de hacer un 'apt-get update' antes del install?

puede ser que al actualizar las listas de paquetes intente arreglar lo que te falta.

Si eso no funciona, probaría haciendo un backup del directorio /var/lib/apt/list y renombrandolo. Despues un apt-get update para que vuelva a bajar las listas de paquetes.

---

### Post by User21 on 2007-11-24
Lo solucioné renombrando el archivo al cual hace alusión el error, y luego haciendo un update! Volvió a descargar el archivo el cual parecía estar corrupto!

Gracias por tu ayuda, de todas formas!

PD: Como le pongo [SOLVED] al Topic ??? :P

---

### Post by sajnox on 2007-11-24
> **User21 said:**
> Lo solucioné renombrando el archivo al cual hace alusión el error, y luego haciendo un update! Volvió a descargar el archivo el cual parecía estar corrupto!

Gracias por tu ayuda, de todas formas!
 
PD: Como le pongo [SOLVED] al Topic ??? :P

Al inicio del thread tenes "thread tools" ahi tenes la opcion de marcar solved

Este ya lo hice 

Saludos

---

