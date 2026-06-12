---
title: "Imposible crear particion extendida"
date: 2007-09-08
forum: Argentina Team
---

### Post by kha0s101 on 2007-09-08
[COLOR="Green"]Hola. Tengo en el disco un espacio sin asignar que no puedo particionar como extendida, sino que me da solo la opción de crear una partición primaria, cosa que no es. 

[Aquí]("http://img356.imageshack.us/my.php?image=pantallazoic1.png") se puede ver el estado del disco, 

Si a pesar de ello aplico los cambios, siempre da error al no poder crear una partición primaria, aún cuando si puede crear la partición vacía :confused:

Extrañamente, luego de los intentos fallidos, [sí genera una partición]("http://img365.imageshack.us/my.php?image=pantallazo2hx8.png") aunque solo puedo verla en Lost+Found con una cruz roja sobre la carpeta y en sus propiedades dice que el contenido es ilegible. En otras palabras, no puedo usar ese espacio.

Mi idea original era destinar ese espacio para descargar cosas, guardar documentos, música, etc. Por lo que leí, es posible enlazar simbólicamente con lo que puedo usar una partición en una sola carpeta, por ejemplo, pero no tengo idea de como se hace.

Desde ya, agradezco la ayuda que puedan brindarme con estos 2 problemas.

Saludos.
[/COLOR]

---

### Post by juanman on 2007-09-08
Uf, te gusta complicarte con muchas particiones como a mi :D

> Extrañamente, luego de los intentos fallidos, sí genera una partición aunque solo puedo verla en Lost+Found con una cruz roja sobre la carpeta y en sus propiedades dice que el contenido es ilegible. En otras palabras, no puedo usar ese espacio.

Proba formateando la particion con:
sudo mkfs.ext3 /dev/sda4

> Mi idea original era destinar ese espacio para descargar cosas, guardar documentos, música, etc. Por lo que leí, es posible enlazar simbólicamente con lo que puedo usar una partición en una sola carpeta, por ejemplo, pero no tengo idea de como se hace.

Podes hacer 2 cosas:
1) Montar la particion en una carpeta (debes crearla primero) en tu home directamente, eso lo editas en el archivo /etc/fstab
Por ej, agregas esta linea:
/dev/sda4 /home/usuario/Musica     ext3    defaults        0       2
Q te va a montar la particion en la carpeta /home/usuario/Musica. Tenes q reiniciar para q se hagan los cambios o escribi sudo mount -a

2) Otra (como hago yo) es montar la particion en otro lado, por ej en /media/datos (tambien debes modificar el fstab), y desde ahi hacerle los enlaces simbolicos. Despues de montar, creas la carpeta /media/datos/musica, etc. Luego haces los enlaces: yo lo hago desde konqueror (tengo kubuntu) arrastrando o copiando /media/datos/musica hasta soltar en /home/usuario/ me pregunta q quiero hacer y pongo "enlazar aqui". En nautilus no me acuerdo como se hace, pero busca en google q te va a salir. Tambien lo podes hacer desde consola con ln. Podes crear todos los enlaces q quieras asi q te recomiendo esta segunda opcion...

Bueno, si tenes dudas chifla...
Saludos

---

### Post by kha0s101 on 2007-09-08
[COLOR="Green"]Muchas gracias!! Ahora mismo me siento a probar :)

Si solo pudiera reemplazar al Pinnacle Studio, borraría todas las particiones, jeje... bah, mentira, me gusta jugar con las particiones!!! :wink:

Saludos.
[/COLOR]

---

### Post by Mister X on 2007-09-08
El candado al lado de cada particion significa que no podes modificarla, por lo tanto no podes agregar una particion extendida porque para eso tenes que modificar una primaria. Igualmente no tendrias que tener fproblemas en agregar una primaria (/dev/sda4)
No me acuerdo bien porque aparecen bloqueadas, puede ser porque estan montadas, proba de iniciar con un live-cd y hacelo sin montar las unidades, te deberia permitir agregar una extendida, en este caso /dev/sda10

saludos

---

### Post by UBUjuan on 2007-09-10
Donde dice /dev/sda2 extended esa es una partición extendida, y solo podes tener una. Si no la podés redimencionar es porque esta montada, y también las unidades logicas. Ademas hay otro problema tenes que mover o sacar la particion primaria contigua /dev/sda3 o si no tampoco podes redimencionar la extendida.

---

### Post by kha0s101 on 2007-09-11
[COLOR="Green"]Perdón por la demora en contestar. 

Efectivamente, me ha sido imposible, no solo crear la partición extendida sino también la primaria. Como afirmó UBUjuan, solo podía hacer algo si modificaba sda3 así que opté por lo más rápido que fue eliminar sda3 para formatear agregando el espacio sin asignar.

Estoy muy contento con el funcionamiento de Ubuntu. Es en verdad un SO muy bien hecho.

Gracias a todos por la ayuda. Espero alguna vez poder hacer yo lo mismo y devolver el favor!!

Saludos[/COLOR]

---

### Post by kha0s101 on 2007-09-11
[COLOR="Green"]Por cierto, acabo de notar recientemente que apareció la dichosa Lost+Found. Esto implica que Linux encuentra problemas en la partición?

Intentaré, logueado como root, eliminar la carpeta o algo, a ver que sucede.

Saludos.[/COLOR]

---

### Post by euzkoarima on 2008-04-12
Como tenía una partición sin usar en la que iba a instalar algun otro SO para probar, y finalmente convencido que no tengo tiempo, decidí formatearla y usarla. Busqué en el foro y encontré este thread, me sirvió y llegué exactamente a lo mismo.
Lo que quiero agregar es como solucioné lo del candado, etc.
abrí un terminal en el directorio donde monto la nueva partición y

> sudo rmdir lost+found
sudo chown miuser:migrupo .

Obviamente migrupo es mi grupo por defecto (que se llama igual que miuser).
A partir de ahí lo monta sin problemas y todo bien.

Saludos

---

