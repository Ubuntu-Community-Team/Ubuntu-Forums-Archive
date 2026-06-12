---
title: "Ubuntu se cierra y..."
date: 2007-07-26
forum: Argentina Team
---

### Post by jajajavi on 2007-07-26
La situación es la siguiente, estoy trabajando con el [Inkscape]("http://www.inkscape.org/"), suenan unos mp3 en Amarok y navego con firefox, entonces Ubuntu se empieza a poner como "tartamudo", todo proceso tarda mucho y de repente pantalla negra... No hay Alt+Ctrl+tecla que me saque de la oscuridad total, no puedo reiniciar X ni salir a ninguna consola, simplemente una fría pantalla negra. Me pasó varias veces últimamente y he dejado casi una hora la pc encendida esperando en vano que se "reanime" para no apretar el botón reset. Generalmente termino reseteando y todo vuelve a la normalidad. Esto me pasa con y sin Beryl activado. Es una AMD 64 1Gb Ram Ubuntu Feisty (kernel 2.6.20-16 generic) con escritorio Gnome tuneado, nVidia GeForce FX5500 y 2 monitores. ¿Qué puedo hacer para detectar y arreglar el problema? Antes llamaba a un "técnico" o reinstalaba windows, ahora me gustaría poder resolverlo y en lo posible no romperle las OO al amigo nerd que me inició en esto. Gracias a todxs, cualquier ayuda es bienvenida.

---

### Post by lugonesjoaquin on 2007-07-26
La verdad que ni idea, yo solo se que Ubuntu se basa en Debian Experimental, el cual contiene paqueteria nueva y no testeada normalmente con muchos bugs, esa es la causa muchas veces de la inestabilidad de Ubuntu. :)

---

### Post by kowal on 2007-07-26
Parece un bug. Puede ser que algún programa por alguna extraña razón se dispare un "memory leak" que se morfe toda la memoria.. o algo que ocupe todo el % de CPU.. andá monitorizando los procesos con algún monitor del sistema como "top" (o htop, que es mejor) a ver si salta que puede ser..

---

### Post by MeduZa on 2007-07-26
> **jajajavi said:**
> La situación es la siguiente, estoy trabajando con el [Inkscape]("http://www.inkscape.org/"), suenan unos mp3 en Amarok y navego con firefox, entonces Ubuntu se empieza a poner como "tartamudo", todo proceso tarda mucho y de repente pantalla negra... No hay Alt+Ctrl+tecla que me saque de la oscuridad total, no puedo reiniciar X ni salir a ninguna consola, simplemente una fría pantalla negra. Me pasó varias veces últimamente y he dejado casi una hora la pc encendida esperando en vano que se "reanime" para no apretar el botón reset. Generalmente termino reseteando y todo vuelve a la normalidad. Esto me pasa con y sin Beryl activado. Es una AMD 64 1Gb Ram Ubuntu Feisty (kernel 2.6.20-16 generic) con escritorio Gnome tuneado, nVidia GeForce FX5500 y 2 monitores. ¿Qué puedo hacer para detectar y arreglar el problema? Antes llamaba a un "técnico" o reinstalaba windows, ahora me gustaría poder resolverlo y en lo posible no romperle las OO al amigo nerd que me inició en esto. Gracias a todxs, cualquier ayuda es bienvenida.

creo que hace mucho me paso algo asi  y fue por una modificacion que hice en algo (no recuerdo que) pero lo repare cambiando ese no me acuerdo que :(
si me acuerdo que era te digo

---

### Post by Hei Ku on 2007-07-26
A mi las veces que me paso eso fue por el firefox, pudiste abrir el system monitor y ver que era?

Proba apretando CTRL+ALT+F1, y esperar a que arranque la consola. logueate, y pone "top"
Eso te va a mostrar si algun proceso se esta comiendo la CPU.

Tambien podes fijarte en daemon.log si habia algo corriendo justo a esa hora. Esta en /var/log/daemon.log

---

