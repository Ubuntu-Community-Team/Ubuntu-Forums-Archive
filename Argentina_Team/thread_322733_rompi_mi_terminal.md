---
title: "rompi mi terminal?"
date: 2006-12-20
forum: Argentina Team
---

### Post by Nemesis Teufel on 2006-12-20
Tengo un problema con la consola.. cuando quiero hacer un: sudo gedit "crear nuevo archivo" no puedo.. no me crea nada.. y me deja abajo el espacio en blanco y no ponga lo q ponga en la consola no me hace caso..
tengo q cerrarla y abrirla para que me funque.

que caranchos pasa?

---

### Post by ubuntu27 on 2006-12-21
Como  sudo gedit "crear nuevo archivo" ?


Segun veo el manual de gedit, nuevo documento es:

      --new-document
              Create a new document in an existing instance of gedit.

```
gedit --new-document
```


Y de cierto, por que estas tratando de usar gedit en el terminal? 
Recuerda que el launcher de gedit esta en el Menu Aplicaciones/Accesorios/Editor de Texto (gedit) 


 de cierto, un tip o truco para ti:

:KS  Cuando quieras leer el manual para alguna aplicacion especifica en el terminal, escribe "man" (man de Manual) seguido con el nombre de la aplicacion.

Ejemplo: Manual de gedit

```
man gedit
```

otro ejemplo: Manual de Aptitude

```
man aptitude
```

Eso te ayudara bastante :)


> no me crea nada.. y me deja abajo el espacio en blanco y no ponga lo q ponga en la consola no me hace caso..

Cunado executas un programa que no sea el terminal/konsola DESDE el terminal (ejemp: gedit, gaim, etc), no podras usar el terminal sino hasta que cierres la applicacion externa que ejecutaste desde el terminal.
Si ejecutaste n programa y necesitas usar el terminal, pero no quieres cerrar el programa executado, entonces lo que puedes hacer es crear un nievo "tab" creo que en espanol se llama "pesteña" 

En el terminal, anda al manu Archivo y escojoes "Abrir Tab"

---

### Post by Nemesis Teufel on 2006-12-27
Creo que no entendi un pomo.

A ver.. yo quiero modificar mi "/etc/apt/sources.list"

Si la memoria no me falla, antes lo hacia desde Terminal..

Si hago: gedit /etc/apt/sources.list
Me abre mi sources.list pero no puedo modificar nada.. entonces agrego el sudo..
reintento con: sudo gedit /etc/apt/sources.list
y no pasa nada.. no me lo abre y no me dice nada en terminal.. es como si no hubiese escrito nada.

Con el editor de textos es lo mismo.. puedo abrir la sources.list pero no modificar. :(

---

### Post by Dr. Falken on 2006-12-28
proba intentandolo abrir con un editor de texto en modo consola, ej, nano....

sudo nano /etc/apt/sources.list

En lo personal uso vi, pero a muchisima gente le resulta incómodo. Pero muchas veces el problema pasa pq las X rechazan abrir ventanas con otro propietario al que inicio la sesion (al abrir un gedit con sudo, la ventana de gedit tiene permisos de root, x ende, el propietario es root).

en todo caso, para ver si el problema viene x ahí, en el terminal, antes de hacer el sudo gedit archivo, hacé esto:

xhost +127.0.0.1

Y si abre correctamente, el problema pasa x ahí... aunque no me acuerdo cómo se resolvía en forma permanente.


El doc

---

### Post by ubuntu27 on 2006-12-28
> **Nemesis Teufel said:**
> Creo que no entendi un pomo.

A ver.. yo quiero modificar mi "/etc/apt/sources.list"

Si la memoria no me falla, antes lo hacia desde Terminal..

Si hago: gedit /etc/apt/sources.list
Me abre mi sources.list pero no puedo modificar nada.. entonces agrego el sudo..
reintento con: sudo gedit /etc/apt/sources.list
y no pasa nada.. no me lo abre y no me dice nada en terminal.. es como si no hubiese escrito nada.

Con el editor de textos es lo mismo.. puedo abrir la sources.list pero no modificar. :(


Haber, trata de abair el gedit con gksudo

```
gksudo gedit
```

```
gksudo gedit /etc/apt/sources.list
```


gksudo es lo mismo que sudo pero para aplicaciones que no sean el terminal (que tengan GUI).



* gksudo usa configuracion de root + super user
* sudo usa configuracion del usuario actual + poder super user

Mas detalles en Ingles: [http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

---

### Post by jpmorelli on 2006-12-28
Yo conocía gksu pero parece que abrevia gksudo porque lo probé y tambien anda.

---

