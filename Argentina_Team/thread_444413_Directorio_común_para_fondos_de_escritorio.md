---
title: "Directorio común para fondos de escritorio"
date: 2007-05-15
forum: Argentina Team
---

### Post by electronpositivo on 2007-05-15
¡Buenas tardes!

Me gustaría saber en qué lugar se guarda la configuración por defecto al crear un nuevo usuario. Por ejemplo, el fondo es el mismo para cada usuario la primera vez que inicia sesión. ¿Esto se puede modificar?

También quisiera saber si existe alguna forma de agregar nuevos fondos y que estos pueda elegirlo cualquier usuario (que le aparezca como uno más en las preferencias del fondo del escritorio).

Gracias

---

### Post by fetova on 2007-05-15
Se puede modificar dando clic derecho en el escritorio y en cambiar fondo de escritorio...

Todas la configuraciones estan en el home de cada usuario...

puedes solo ponerlo en /usr/share/backgrounds/

ahi estan

lo demas no se :)

---

### Post by electronpositivo on 2007-05-22
He probado en /usr/share/backgrounds pero no aparecen en la lista de fondos (clic derecho en el escritorio y en cambiar fondo de escritorio) de todos los usuarios... debo hacer algo más???

---

### Post by electronpositivo on 2007-05-25
Tengo esto: /home/NOMBREUSUARIO/.gconf/desktop/gnome/background/%gconf.xml

 En este fichero se guardan los fondos personalizados que cada usuario elige y que tiene en su lista de fondos.

 Dudas:

    * Aquí no están los 2 fondos que aparecen por defecto, el de "Simple ubuntu" y el otro de "Smooth chocolate". Sabéis dónde está el fichero de configuración que tiene esto?
    * Si modifico este fichero, escribiendo manualmente nuevas rutas, aparece en el listado de fondos del usuario actual, si quiero que lo tengan todos, lo puedo copiar al fichero de configuración que está en el home de cada usuario... hay una forma más rápida (un fichero común a todos) para hacerlo?

Espero que quede más claro qué es lo que pretendo.

 Gracias

---

### Post by Kantier on 2007-05-25
no era /usr/share/wallpapers el directorio de los fondos de escritorio?

---

### Post by fetova on 2007-05-25
> **Kantier said:**
> no era /usr/share/wallpapers el directorio de los fondos de escritorio?

mmm. No. Es /usr/share/backgrounds


 > **electronpositivo said:**
> 	Tengo esto: /home/NOMBREUSUARIO/.gconf/desktop/gnome/background/%gconf.xml

En este fichero se guardan los fondos personalizados que cada usuario elige y que tiene en su lista de fondos.

Dudas:

* Aquí no están los 2 fondos que aparecen por defecto, el de "Simple ubuntu" y el otro de "Smooth chocolate". Sabéis dónde está el fichero de configuración que tiene esto?
* Si modifico este fichero, escribiendo manualmente nuevas rutas, aparece en el listado de fondos del usuario actual, si quiero que lo tengan todos, lo puedo copiar al fichero de configuración que está en el home de cada usuario... hay una forma más rápida (un fichero común a todos) para hacerlo?

Espero que quede más claro qué es lo que pretendo.

Gracias

ni idea :( aunque puedes checar algo asi en /usr/share ahi es el directorio en el que se comparte todo, en algun sitio dentro debe de estar

Saludos y ojala lo encuentres :)

---

### Post by juako on 2007-06-14
los que yo uso son /usr/share/backgrounds (y subdirs) y /usr/share/pixmaps/wallpapers*, aunque tambien agregué otros en mi directorio de datos personal, con "wallpaper-tray" los podes cambiar automaticamente

---

