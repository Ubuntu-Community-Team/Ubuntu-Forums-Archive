---
title: "Azureus en Ubuntu 7.10"
date: 2007-11-18
forum: Argentina Team
---

### Post by Oktubre on 2007-11-18
Buenas,

me empezo a fallar el Azureus luego de que actualice a Ubuntu 7.10.

Cuando lo ejecuto me da el siguiente error:

[I]$ azureus 
changeLocale: *Default Language* != English (United States). Searching without country..
changeLocale: Searching for language English in *any* country..
changeLocale: no message properties for Locale 'English (United States)' (en_US), using 'English (default)'
Exception in thread "main" java.lang.UnsupportedClassVersionError: org/eclipse/swt/widgets/Display (Unsupported major.minor version 49.0)
        at java.lang.ClassLoader.defineClass0(Native Method)
        at java.lang.ClassLoader.defineClass(ClassLoader.java:539)
        at java.security.SecureClassLoader.defineClass(SecureClassLoader.java:123)
        at java.net.URLClassLoader.defineClass(URLClassLoader.java:251)
        at java.net.URLClassLoader.access$100(URLClassLoader.java:55)
        at java.net.URLClassLoader$1.run(URLClassLoader.java:194)
        at java.security.AccessController.doPrivileged(Native Method)
        at java.net.URLClassLoader.findClass(URLClassLoader.java:187)
        at java.lang.ClassLoader.loadClass(ClassLoader.java:289)
        at sun.misc.Launcher$AppClassLoader.loadClass(Launcher.java:274)
        at java.lang.ClassLoader.loadClass(ClassLoader.java:235)
        at java.lang.ClassLoader.loadClassInternal(ClassLoader.java:302)
        at org.gudy.azureus2.ui.swt.Main.<init>(Main.java:147)
        at org.gudy.azureus2.ui.swt.Main.main(Main.java:162)
[/I]

Tambien probe con las diferentes versiones de Java que tengo instalado. En todos los casos no llega a abrir el Azureus.

[I]There are 4 alternatives which provide `java'.

  Selection    Alternative
-----------------------------------------------
*+        1    /usr/lib/j2se/1.4/bin/java
          2    /usr/bin/gij-4.1
          3    /usr/bin/gij-4.2
          4    /usr/lib/jvm/java-gcj/jre/bin/java[/I]

Alguna idea? A alguien le sucede lo mismo?

Gracias, 

Saludos,

---

### Post by facundocorradini on 2007-11-18
pues ni idea, pero te recomiendo usar Deluge en lugar de azureus, es mil veces mas liviano y anda muy bien

---

### Post by clasificado on 2007-11-19
> changeLocale: *Default Language* != English (United States). Searching without country..

Debe ser un quilombo de locales, que con Gutsy cambiaron, y debieron haberle hecho perder el coco.

trata borrando la carpeta ~/.azureus, ejecutas nuevamente azureus, eso me funcionó a mi.

clasificado

---

### Post by Oktubre on 2007-11-19
Gracias a ambos!

Ayer instale el Azureus 3.0.3 y por el momento anda bien.

Saludos,

---

### Post by faktorqm on 2007-11-19
ok, igual por el bien de tu espacio en memoria ram y consumo de recursos, te recomiendo deluge. 

[http://deluge-torrent.org/](http://deluge-torrent.org/)

salu2!

---

### Post by marianom on 2007-11-19
Deluge está buenísimo y en Python. Two thumbs up!

---

### Post by Oktubre on 2007-11-19
Gracias, Ya lo estoy instalando, asi que lo empezare a utilizar...

Consulta: cuando se instalan aplicaciones (como deluge / azureus) desde el .deb, hay alguna manera luego de desinstalarlas? 
Es conveniente desinstalarlas o se corre el riesgo que perder alguna dependencia que sea util ?

Saludos,

---

### Post by marianom on 2007-11-19
> **Oktubre said:**
> Consulta: cuando se instalan aplicaciones (como deluge / azureus) desde el .deb, hay alguna manera luego de desinstalarlas?

Si es desde un .deb, de la misma forma que desinstalás tus otras aplicaciones. El método más sencillo Synaptic. 

> **Oktubre said:**
> Es conveniente desinstalarlas o se corre el riesgo que perder alguna dependencia que sea util ?

S estamos hablando solo de estas dos aplicaciones, no, no parece que vayas a perder nada trascendente. Cualquier problema avisa.

---

### Post by facundocorradini on 2007-11-19
a propósito, si vas a usar Deluge te recomiendo instalarlo desde los repositorios y no desde un deb.

De esta forma queda más integrado al sistema (te avisa de actualizaciones y eso), ademas te avitas cualquier problema.  
El soft de los repositorios ademas cuenta con la ventaja de estar revisado, por lo que podés estar mas tranquilo que con paquetes deb. 

Te recomiendo que siempre que sea posible instales el software desde los repositorios

---

### Post by Oktubre on 2007-11-19
Al decir desde los repositorios, te referis desde "Add/Remove..." ? Porque lo busque ahi y no lo encontre, entonces instale el .deb. Me gustaria instalarlo desde los repositorios asi me avisa de las actualizaciones, etc.

Saludos,

---

### Post by marianom on 2007-11-19
Según recuerdo, Gutsy es la primera versión que trae Deluge. Como es natural, está algunos releases atrás.

---

