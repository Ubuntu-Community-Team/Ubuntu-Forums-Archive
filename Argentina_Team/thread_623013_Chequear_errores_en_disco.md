---
title: "Chequear errores en disco"
date: 2007-11-25
forum: Argentina Team
---

### Post by User21 on 2007-11-25
Que aplicación **GRÁFICA** conocen para chequear y reparar errores en los discos ? He oído que si se detectan ciertos errores, Linux bloquea el acceso a los sectores defectuosos. Cómo hacerlo en Ubuntu? Quién puede aportar algo de información?

---

### Post by faktorqm on 2007-11-26
che buske y buske y no encontre nada :S

salu2!

---

### Post by User21 on 2007-11-26
Lo que cabe destacar es que en Linux, el fsck chequea cada 20 o 30 veces que montaste un disco, su integridad; en resumen: no es necesario DESFRAGMENTAR, ya que el sistema se encarga de tener todo en orden automaticamente, ademas de que los sistemas de archivos en Linux tienen mayor consistencia y seguridad frente a posibles errores logicos y fisicos. De todas formas, a veces, obtengo, en medio de cualquier proceso, errores de lectura en ciertos bloques. Por esto, mediante la observacion, queria ver si podia identificar aquellos sectores donde siempre ocurren errores, y evitar su lectura escritura. Eso, presuponiendo que el error viene por alli... xD 

Sino, la otra posibilidad que contemplaba, es que alguien le esta haciendo VUDU a mi disco duro, lo cual es una opcion que hay que tener siempre presente. Tecnicamente, se le puede hacer vudú a cualquier cosa... 
Asi de versatil es la magia negra. xD

---

### Post by faktorqm on 2007-11-26
se... a mi el fschk me tiene las ****las por el piso, no se por que me saca del splash y me muestra CADA VEZ QUE ARRANCO la compu que el sistema de archivos tiene una fecha del FUTURO y que me lo arregló satisfactoriamente!............. GRACIAS VIEJA! igual no queria que me hagas nada, solo arrancar rapido :D xD

we... te olvidaste de aclarar en tu post que es mas rapido y mas confiable que fat16/32 o ntfs, por que reiserfs y xfs van josha. :D

como desactivo fschk? sino da para hecharlo: como hago que no me escriba la fecha del futuro? es que mi pc va tan rapido que me pone fecha de mañana XDDDDDDDDDDDDDDD ok. 
salu2!

---

