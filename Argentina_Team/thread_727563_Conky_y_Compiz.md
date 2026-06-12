---
title: "Conky y Compiz"
date: 2008-03-17
forum: Argentina Team
---

### Post by newtonfn on 2008-03-17
Hola  !!

Luego de ver tantos screenshots donde usan conky me dieron ganas de tenerlo yo tambien en mi computadora, y usando el conky que esta en los repositorios y un poco de ayuda de internet lo tengo funcionando bastante bien.

Solo hay una cosa que me molesta actualmente, y es que no puedo arrastrar iconos del escritorio a esa parte de la pantalla. Si pongo un icono en donde esta conky, ese ícono desaparece bajo la ventana de conky

Estoy usando Ubuntu Gutsy, con los efectos de escritorio activados y honestamente quiero seguir con ellos (me gustan mucho jeje)

Gracias a cualquiera que pueda guiarme en la búsqueda de la solución.

---

### Post by oktubrer on 2008-04-14
Quizas un poco tarde, pero si no encontraste nada:

[http://ubuntuforums.org/showthread.php?t=658861](http://ubuntuforums.org/showthread.php?t=658861)

Básicamente, en el .conkyrc agregar:

own_window yes
own_window_type override
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager

Aparentemente tenés que iniciarlo como ventana, aunque con esas opciones a la vista quedaría igual.

---

### Post by MeduZa on 2008-04-14
> **newtonfn said:**
> Hola  !!

Luego de ver tantos screenshots donde usan conky me dieron ganas de tenerlo yo tambien en mi computadora, y usando el conky que esta en los repositorios y un poco de ayuda de internet lo tengo funcionando bastante bien.

Solo hay una cosa que me molesta actualmente, y es que no puedo arrastrar iconos del escritorio a esa parte de la pantalla. Si pongo un icono en donde esta conky, ese ícono desaparece bajo la ventana de conky

Estoy usando Ubuntu Gutsy, con los efectos de escritorio activados y honestamente quiero seguir con ellos (me gustan mucho jeje)

Gracias a cualquiera que pueda guiarme en la búsqueda de la solución.

hola, estoy setiando mi conky desde hace unos dias y la vercion en los repositorios no esta completa, yo compile la mia y ahora me anda bien, muchas de las variables de conky no estan en la vercion de los repo
pone en la linea de comando conly -V (v mayuscula) y te sale la vercion
yo tengo
Conky 1.5.1 compiled Sun Apr  6 02:45:12 EDT 2008 for Linux 2.6.24.4 (i686)
Si necesitas el .deb te lo puedo pasar porque lo tengo aca. pero solo para i686

Por lo que preguntaste, conky no tiene fondos tranparentes reales, solo copia la imagen de fordo de donde esta puesto el y se la pone de fondo, osea que lo que este abajo de el no se veria, creo que si lo pones en modo ventana entonces ahi si funfiona, pero le tendrias que quitar los decoradores.
proba, yo debajo de conky no pongo nada, asumo esa zona como una zona para conky y listo pero si vos queres meter cosas ahi vas a tener que probar eso que te dijeron mas arriba, o con la opcion own_window_type  normal o desktop
o directamente: own_window no

---

