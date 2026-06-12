---
title: "Scripts"
date: 2008-03-22
forum: Argentina Team
---

### Post by MaReaDo^ on 2008-03-22
yoce hice un script que decia algo asi:

#!/bin/bash

mount '/dev/sda1' '/windows'
mount --bind '/windows/Documents and Settings/Facundo/Mis documentos' '/home/facundo/Mis documentos en FacundoWindows'
mount --bind '/windows/Documents and Settings/Facundo/Mis documentos/Mi música' '/home/facundo/Música'

despues hice un lanzador en la barrita de arriba:

'/home/facundo/Scripts/Montar'

y no funcionaba asi que le agregue sudo adelante

pero no pasa nada
puse aplicacion en terminal a ver que me decia y me dice:

"No se ha podido lanzar la aplicacion.
Ha ocurrido un error al ejecutar el proceso hijo <-x> (No existe el fichero o directorio)

pero si pongo en un terminal:

$ sudo '/home/facundo/Scripts/Montar'

funciona

que puede estar pasando?

---

### Post by faktorqm on 2008-03-24
Le pusiste permisos de ejecucion el archivo ese? 
En el lanzador tambien podes escribir "sh /blablabla/Montar".
Por que montas asi las cosas y no con el fstab? salu2!

---

### Post by leo_rockway on 2008-03-24
> **faktorqm said:**
> Le pusiste permisos de ejecucion el archivo ese?

chmod +x nombrescript

Sin permisos de ejecución eso no va, es tal como dijo faktorqm.

---

### Post by MaReaDo^ on 2008-03-25
sisi, si tien epermisos de ejecusion
no uso ftab porque, nose
porque no quier oque se monte solo, quiero monstarlos y desmontarlos cuando quiero
el sh antes funciono :D
se me hace que no funcionaba sin el sh, porque tengo un problema con los scripts, se me habia puesto que wine me los abra por defecto, y no se cual esl que los tiene que abrir por defecto
en fin, ya funciono, gracias :D


edit: reinicie y no funciono mas xD tendra que ver con el sudo? pasa que sin sudo no me lo monta y si pongo en el script sudo lo mismo pasa

---

### Post by faktorqm on 2008-03-25
si capo! mount necesita sudo si o si. Salu2!

---

### Post by MaReaDo^ on 2008-03-25
tiene puesto el sudo, tengo que poner algo como para que me pida la clave el lanzador?

---

### Post by faktorqm on 2008-03-25
y proba con "gksudo" a ver que pasa, salu2!

---

### Post by MaReaDo^ on 2008-03-27
cual es la diferencia entre sudo y gksudo?

---

### Post by faktorqm on 2008-03-27
Que sudo es en modo texto, gksudo es el sudo, pero para el entorno grafico en GTK2+ o GTK+ (gnome) (en lugar de pedirte la contraseña con una oracion, lo hace con una ventana) y kdesu es el sudo pero para el entorno grafico QT, es decir, para KDE, ke cumple la misma funcion que gksudo. Salu2!!

---

### Post by MaReaDo^ on 2008-03-27
ahi con el gksudo solucione todo
muchas gracias :D

---

