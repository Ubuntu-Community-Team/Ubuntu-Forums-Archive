---
title: "Firefox en inglés"
date: 2007-10-19
forum: Argentina Team
---

### Post by hernan blau on 2007-10-19
Con Gutsy se me instaló el Firefox en inglés, aunque elegí con la instalación nuestro idioma. ¿Saben cómo hacer para que esté en castellano? Gracias.

---

### Post by facundocorradini on 2007-10-19
Creo q no estabas conectado a internet mientras instalabas, no es así?...

Entonces lo que pasa es que se instala el sistema en español, pero los programas continuan en ingles (sería imposible incluir en un cd todos las traducciones para todos los programas para todos los idiomas...)


La solución es que instales el paquete 

language-pack-es 

mediante sinaptic o bien por apt (apt-get install language-pack-es), con eso todo tu soft queda traducido al español.

---

### Post by hernan blau on 2007-10-19
Gracias Facundo. Es cierto que instalé sin internet, pero esos paquetes que indicás los tengo instalados según acusa Sinaptyc. Veré. De última reinstalo con banda ancha.

---

### Post by facundocorradini on 2007-10-19
oops! le pifé de paquete... 


pero si te fijás la descripción de synaptic del que te pasé, 
```
translations for language Spanish; Castilian 
Translation data for all supported packages for:
Spanish; Castilian

This package provides the bulk of translation data and is updated
only seldom. language-pack-es provides frequent
translation updates, so you should install this as well.

Please note that you should install language-support-es
to get full support for this language (spell checkers, OpenOffice and
Mozilla locale packages, etc.).
```

Fijate el último párrafo, podés ver que en tu caso lo que necesitas es el paquete 

**language-support-es**

fijate si eso lo arregla

---

### Post by margori on 2007-10-19
Por lo de reinstalar, no creo que poner todos uts programas en castellano, incliso creo que terminaras en el mismo lugar en el que estas ahora.

Te recomiendo no reinstalar y buscar la forma de instalar los paquetes de idiomas. He aprendido desde que estoy en linux, que todo tiene solucion sin necesidad de reinstalar (A diferencia del conocido W)

Por otro lado, tambien existe la posibilidad de instalar el castellano desde el mismo Firefox.

Eso es todo y espero haber ayudado.

---

### Post by hernan blau on 2007-10-19
Gracias Facundo y Margory. Instalé el último archivo que indicó Facundo, rebooté y, listo, la lengua de Cervantes me acompaña.

---

### Post by JoACoV on 2007-10-19
[http://ubuntuforums.org/showthread.php?p=3572371#post3572371](http://ubuntuforums.org/showthread.php?p=3572371#post3572371)

vean aca

---

### Post by marcesneibrun on 2007-10-20
GENTE TRATE DE INSTALAR EL PAQUETE Q DIJO FACUNDO LENGUAGE-ES Y ME TIRO UN ERROR AHORA NO PUEDO ENTRAR A SYNAPTIC NI HACER UPDATE NI UPGRADE, LES TIRO EL ERROR ME PUEDEN AYUDAR PLEASE


E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.



GRACIAS MARCELO

---

### Post by marcesneibrun on 2007-10-20
> **marcesneibrun said:**
> GENTE TRATE DE INSTALAR EL PAQUETE Q DIJO FACUNDO LANGUAGE-PACK-ES Y ME TIRO UN ERROR AHORA NO PUEDO ENTRAR A SYNAPTIC NI HACER UPDATE NI UPGRADE, LES TIRO EL ERROR ME PUEDEN AYUDAR PLEASE


E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.



GRACIAS MARCELO

EL PAQUETE Q QUISE INSTALAR ES LANGUAGE-PACK-ES, AHORA NO PUEDO ACTIVAR EL SYNAPTIC

---

### Post by Hei Ku on 2007-10-20
pone:

sudo dpkg --configure -a

para corregir el problema.

---

### Post by marcesneibrun on 2007-10-20
puse lo q me dijiste y me tira lo siguiente:

dpkg: opción --configure-a desconocida

Escriba dpkg --help para ayuda sobre instalar y desinstalar paquetes [*];
Use `dselect' o `aptitude' para una gestión más amigable de los paquetes;
Escriba dpkg -Dhelp para una lista de los valores de depuración de dpkg;
Escriba dpkg --force-help para una lista de opciones para forzar cosas;
Escriba dpkg-deb --help para obtener ayuda sobre manipulación de archivos .deb;
Escriba dpkg --license para ver la licencia (GPL de GNU), el copyright y la
ausencia de garantía [*].

Las opciones marcadas con [*] producen una salida extensa,
¡fíltrela con `less' o con `more'!


en synaptic me tira el mismo error anterior

---

### Post by Hei Ku on 2007-10-20
probaste con un espacio entre --configure y -a? :p

---

