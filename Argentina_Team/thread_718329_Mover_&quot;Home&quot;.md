---
title: "Mover &quot;/Home&quot;"
date: 2008-03-08
forum: Argentina Team
---

### Post by kha0s101 on 2008-03-08
[COLOR="DarkGreen"]Hola. Abro este post porque creo que el tema para Ubuntu 7.10 al menos no fue tratado (bah, quizás yo no lo encontré). Deambulé guiado por San Google, en busca de soluciones pero todas diferentes, lo que no termina de tranquilizarme (aunque sé que eso también es lo bueno de Linux!).

El caso es este: luego de instalar Ubuntu 7.10 fui haciendo updates, afinando el sistema según mis gustos, generando documentos y demás. Sin embargo instalé todo según me guiaba el asistente de Ubuntu y no me avivé de usar otra partición para el /Home :mad:

Reajusté con GParted el tamaño de la partición de Ubuntu (/dev/sda3), dejando espacio para la nueva partición (/dev/sda4). La partición está lista para ser usada (formato ext3 montada en /media/disk).

Nota: algo que me extraña es que sda4 **no** aparece en mi fstab...

Sin embargo, aquí viene mi problema: existen muchos métodos para mover el /Home, pero creo que en este foro tendré una perspectiva más cierta de como hacerlo.

Una ayudita? :lolflag:

Saludos.[/COLOR]

---

### Post by korazonku on 2008-03-08
hola.

con respecto a fstab, es normal q no te aparesca esta nueva particion, por q gparted solo creo la particion.
vos tenes q agregarla aparte.

lo q tendrias q hacer a grandes rasgos es copiar toda la carpeta /home a la otra particion osea cp -p -r /home /direccion/de/la/otra/particion (-p es para q se mantengan los permisos y fechas de los archivos y -r le dice al comando q tambien copie lo que tiene adentro) 

luego vas a sistema / Administracion / usuarios y grupos elegis tu usuario y le cambias, en las propiedades, la direccion de su carpeta de home (la direccion de la otra particion)

reinicias la maquina, y probas o directamente un ctrl alt backspace para q reinicie la x (tmb funciona poner cerrar sesion) ante cualquier error ubicas de nuevo el home.

espero q te sirva

---

### Post by Radiobuzz on 2008-03-08
Hola, casualmente yo hice esto ayer. Lo único que tuve que hacer fue crear la partición, copiar ahí todo el contenido del home y luego escribir en el fstab que monte la partición en /home/. De hecho sólo con montarla ahí Ubuntu debería mover los datos, pero es más seguro hacerlo manualmente.

---

### Post by kha0s101 on 2008-03-08
[COLOR="DarkGreen"]Hola.

Muchas gracias por las respuestas. 

Copié los datos y cambié la ubicación del /home pero al reiniciar me dió error porque no aparece la partición en el fstab así que ahora estoy en eso, a ver como va.

Saludos.[/COLOR]

---

### Post by gmunioz on 2008-03-08
Hola kha...:
Este es un sencillo tutorial acerca de como mover /home:

Una vez que tengas creada la partición debes montarla en un directorio de nombre temporario para poder copiar a ella los archivos del  /home original.
Creas el directorio
sudo mkdir /media/hometemp
Montas la partición
sudo mount /dev/nombredelapartición /media/hometemp
Para copiar:
cd /home
sudo cp -ax . /media/hometemp
Esta última linea es la única que sirve para clonar, atención con "." del final.
Ahora montas el nuevo /home previo renombrar el /home viejo.
cd /
sudo mv /home /home.old
sudo mkdir /home
sudo mount /dev/nombredelapartición /home
Ahora tienes que averiguar la UUID de la partición y editar editar el /etc/fstab, para montar la partición al inicio.
sudo vol_id -uuid /dev/nombre de la partición
sudo gedit /etc/fstab
Y añades estas lineas al final.
#/dev/nombredelapartición 
UUID=a673dafc-1032-45c2-a1b4-a615703bdaaf /home reisefs defaults 1 2
Al reiniciar tendrás todo funcionando exactamente igual, pero con particiones separadas.
Una vez que todo esta funcionando bien
Borras el /home.old.
sudo rm /home.old
Saludos.

---

### Post by kha0s101 on 2008-03-09
[COLOR="DarkGreen"]Buenisimo! Lo usé y funcionó perfecto!! Gracias gmunioz, ahora me siento más tranquilo en cuanto a mis datos.

Una última incógnita. Si mañana decido instalar otra versión de Ubuntu desde cero, al tener el /home en una partición separada no borra nada verdad? asumo que lo que hace es solo tomar esa partición y montarla para comenzar a usar.

Saludos y de nuevo, muchas gracias.[/COLOR]

---

### Post by gmunioz on 2008-03-09
Hola kha...:
Efectivamente, ese es el fin de tener un /home en partición aparte, solo montarlo en cada nueva instalación o reinstalación, sin perder configuración ni datos.
Eso sí debes prestar atención a hacer la instalación o reinstalación, siempre con el mismo nombre de usuario y la misma contraseña.
Saludos.

---

### Post by kha0s101 on 2008-03-09
[COLOR="DarkGreen"]Perfectirijillo amiguillo :lolflag:

Muchas gracias por el tip. No sabía lo de conservar la contraseña.

Saludos.
[/COLOR]

---

### Post by dondionisio on 2008-03-11
Mire, yo hei seguido el tutorial 
[que está en esta direción]("http://cartublog.blogspot.com/2007/10/independiza-tu-home.html"), pasito a pasito, y hei logrado hacerlo.
Capaz que a usté le sirve.

Dionisio Rearte
Desperto Informático Crioyo
[www.ciberrancho.com.ar](www.ciberrancho.com.ar)

---

### Post by kha0s101 on 2008-03-12
[COLOR="DarkGreen"]Muchas gracias. Tuto guardado. A probar se ha dicho!

Saludos.
[/COLOR]

---

