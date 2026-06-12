---
title: "[SOLVED] Ayuda con PyGTK"
date: 2007-11-02
forum: Argentina Team
---

### Post by Mauro22 on 2007-11-02
Hola, como andan??


Tengo una duda, hoy estuve buscando por la web y encontre el PyGTK

[http://www.pygtk.org/](http://www.pygtk.org/)



Ahora bien, dice que pygtk viene inluido con Ubuntu, pero al parecer no. lo busque y nada...

En consola puse "py" y luego TAB, y no tengo nada parecido a pygtk.




Entonces me baje el codigo fuente de la web y traté de compilarlo y me tira este error al final:

```
checking for a Python interpreter with version >= 2.3.5... python
checking for python... /usr/bin/python
checking for python version... 2.5
checking for python platform... linux2
checking for python script directory... ${prefix}/lib/python2.5/site-packages
checking for python extension module directory... ${exec_prefix}/lib/python2.5/site-packages
checking for headers required to compile python extensions... not found
configure: error: could not find Python headers

```


Alguien sabe que me falta o que hice mal....


Saludos y Grax por su tiempo!

---

### Post by Hernán-Amaya on 2007-11-02
fijate si tenes instalado el siguiente paquete  python-gtk2, igual algún pythonero te va poder ayudar mas que yo.

---

### Post by Mauro22 on 2007-11-02
Cambiamos de error.!!


Instale python-dev y un par de cosas mas y ahora el error es:

```
checking for PYGOBJECT... configure: error: Package requirements (pygobject-2.0 >= 2.12.1) were not met:

No package 'pygobject-2.0' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables PYGOBJECT_CFLAGS
and PYGOBJECT_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

```


Solucionado, faltaban dependencias

Saludos y Grax!

---

