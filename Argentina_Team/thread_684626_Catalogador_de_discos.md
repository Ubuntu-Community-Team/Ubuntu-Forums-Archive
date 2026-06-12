---
title: "Catalogador de discos"
date: 2008-02-01
forum: Argentina Team
---

### Post by jclevien on 2008-02-01
Hola,

Estoy buscando un catalogador de discos para Ubuntu.
La idea es que sea similar al ADC (Advanced Disk Catalog) pero para Linux.

Necesito que lea archivos comprimidos de los CD y DVD que tengo.

¿Alguien sabe de algún programa recomendable para esta tarea?


Muchas gracias.



Juan

---

### Post by clasificado on 2008-02-01
eeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeee

Alguna vez he visto un Filesystem que hacia ese trabajo: Te indexa los archivos y los deja flotando en un cache, de tal forma que vos ves todos los cds como si estuvieran todo el tiempo, pero cuando lo vas a usar te para y te pide el cd segun su label :). Pero no me acuerdo como se llama... tiene que estar por ahi...

Aunque, por otro lado, supongo que querras algo mas "Ventanoso" :KS

clasificado

---

### Post by spg76 on 2008-02-02
El mejor programa de este tipo que encontré es Gnome Catalog.
Lamentablemente en la versión actual, la 0.3.3, no puede leer archivos dentro de archivos comprimidos, aunque está planeado agregar esta función en la versión 0.4.
Podés ver más info e instrucciones para descargar el programa (tiene una repo para Ubuntu) en [http://gnomecatalog.sourceforge.net/](http://gnomecatalog.sourceforge.net/)

---

### Post by jclevien on 2008-02-03
Hola spg76,

El problema es que hace varios años que no actualizan el producto.
Mirá, voy a ver si hago un rato de tiempo y me hago un catalogador para cubrir mis necesidades.

Muchas gracias.



Juan

---

### Post by nemodot on 2008-02-03
Buscando en la página de Alternativas libres encontré este programa alternativo al que mencionas.

[http://alts.homelinux.net/search.php?type=priv&q=advanced+disk+catalog](http://alts.homelinux.net/search.php?type=priv&q=advanced+disk+catalog)

En el sector de descargas no tiene una versión deb, prueba si aparece en tu synaptic y sino, de ultima tendrás que compilarlo.

---

### Post by spg76 on 2008-02-03
> **jclevien said:**
> Hola spg76,

El problema es que hace varios años que no actualizan el producto.
Mirá, voy a ver si hago un rato de tiempo y me hago un catalogador para cubrir mis necesidades.

Muchas gracias.



Juan

Juan, es cierto que el programa tuvo un período grande de inactividad pero ahora está alojado en Launchpad y lo actualizaron hace poco (de hecho hoy, 3 de febrero subieron la versión 0.3.4.1 a la repo).
No sé cuanto tardarán en implementar lo que necesitás pero podés ir a la página de Launchpad en [https://edge.launchpad.net/gnomecatalog/](https://edge.launchpad.net/gnomecatalog/) y chequear la actividad del proyecto.

---

