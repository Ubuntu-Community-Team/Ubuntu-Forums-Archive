---
title: "Pregunta sobre particiones"
date: 2008-04-25
forum: Argentina Team
---

### Post by alejandro.mc on 2008-04-25
Pregunta no tan rapida pero seguro facil de contestar:

Yo tenia un disco de 70 GB. Agarre 30 GB de esos, los libere, los unallocatee y cree una partición con esos 30 GB libres Primaria Ext3. Hice esto porque necesitaba 30 GB para backupear cosas. Hubiera creado una particion logica pero no se porque Gparted no me lo permitia. Ahora bien, entre de vuelta en Ubuntu, y para entrar en esa particion que cree tengo que hacerlo a través de SU y abrirla por la terminal, de otra forma no se puede abrir (se puede explorar pero no se puede modificar cosas, ni crear carpetas, ni pegarle contenido). Entrando por terminal como root si se puede (nautilus disk y lo abre y puedo backupear cosas).

Pero la pregunta es: si yo instalo ahora en los 40 restantes el nuevo Hardy 8.04 voy a poder acceder a esta otra particion de 30 GB? porque voy a tener que logearme como root, pero va a ser un root distinto (el del nuevo Hardy). Voy a poder pegar contenido en la particion? Copiar contenido de la particion? ya que esto es para lo que principalmente la necesito, de backup.

Muchas gracias gente! Y suerte para todos quienes este instalando Hardy!!!

---

### Post by tzulberti on 2008-04-25
El hecho de que te tengas que loguear como root a la particion de backup tiene que ver con el punto que esta "mal" editado el archivo /etc/fstab. Lo que deberias de ponerle es que la particion en las opciones que sea algo del estilo:
/dev/hdaX /media/hdaX users,rw   0   0 

Si con esas dos opciones no te funciona fijate en "man mount" (en la opcion -o). Para probar si eso te funciono la vas a tener que desmontar como root, y volverla a montar como user normal.


A todos los archivos que hayas escritos en esa particion lo que vas  a tener que hacer es cambiarle el owner (chown), y talvez los derechos (chmod).

---

### Post by alejandro.mc on 2008-04-25
Gracias por contestar. 

Si yo entro en propiedades de ese disco de backup de 30Gb que hice (entro como root) y le pongo en Permisos > Otros, que deje crear y modificar a cualquiera, con eso se soluciona el problema?

Saludos!

---

### Post by srmantis on 2008-04-25
Las particiones son reconocidas automaticamente por ubuntu al instalar el sistema. Pero cuando modificas las particiones con el sistema ya instalado se producen problemas como no tener permiso para escribir o no se monta automaticamente.

Para solucionarlo hay que modificar, como superusuario, el archivo fstab:
sudo gedit /etc/fstab

Antes de cambiar algo, asegurate de saber cual es la particion que quieres modificar:
df -h (o solamente df)

aparece un listado con el nombre de la particion, tamaño, uso y donde estan montadas, por seguridad no modifiques los que estan montados en /,/home,/va/run,/var/lock,/dev,/dev/shm, etc.

Solo las particiones que se montan en /media/"algo" o que no estan montadas. Otra opcion es ver las particiones con el gparted.
por ejemplo, parte del resultado:
/dev/hda1              17G  5,8G   12G  35% /media/winxp
/dev/hda7             9,1G  3,0G  6,1G  34% /media/musica
/dev/hda8             9,7G  1,9G  7,8G  20% /media/multimedia

Ejemplo, yo quiero modificar la particion /dev/hda8, que se monta en /media/multimedia (o tambien puede decir /media/hda8 )

para montar automaticamente una particion debemos parar el montaje que trae en el fstab:
# /dev/hda8
UUID=D8C8D5FOC8D5CCBE /media/hda8     ntfs    defaults,umask=007,gid=46 0       1
modificamos la linea, agregando una almohadilla # para que no use ese modo de montaje:
# /dev/hda8
#UUID=D8C8D5FOC8D5CCBE /media/hda8    ntfs    defaults,umask=007,gid=46 0       1

Ahora agregamos una linea con el montaje:
/dev/hda8 /media/respaldo ntfs defaults,umask=007,gid=46 0 0

y guardar. Al reiniciar el sistema se veran los cambios.

Muy importante, la carpeta respaldo (en este caso) debe ser creada antes, abrimos la terminal:
sudo mkdir /media/respaldo

Entendamos un poco lo que hicimos, mas o menos lo que yo entiendo:
le decimos al sistema que tome la particion /dev/hda8 y que la monte en /media/respaldo
ntfs: el sistema de archivo, tambien lo puedes cambiar por ext3, ext2, etc.
defaults: que tome las opciones por defectos, mejor pregunta a google. Una de ellas es rw: permitir escribir la particion.
umask=007: aqui le damos los permisos, son todo lo contrario a chmod. 000: todos los permisos. 777: ningun permiso (primer numero: usuario dueño, segundo:grupo, tercero : otros usuario)
007: todos los permisos al dueño y al grupo, pero ningun permiso a otros usuarios.

gid=46: esta parte le asigna los permisos al grupo en este caso al grupo 46 que es plugdev, es el que viene por defecto.

Puedes crear un grupo y luego reemplazar el codigo:
sistema-->administracion-->usuarios y grupos:boton gestionar grupo, añadir grupo y seleccionar a los usuarios que estan en el grupo, luego aceptar.
ejemplo: cree el grupo "respaldo", entonces su numero es 1003. ahora modifico el gid=1003 en el archivo fstab. Solo los usuarios que esten el grupo respaldo pueden ver, escribir y ejecutar archivos en la particion.


Importante : para quitar usuarios del grupo plugdev, solo tienes que elegir al usuario, propiedades y en privilegios de usuario, desmarcar la opcion: accedera utomaticamente a dispositivos de almacenamiento externo o modificando el archivo /etc/group

Espero que te sirva la informacion, yo hace 2 dias que me entere de esto porque no podia montar mis particiones y ahora estan funcionando de maravilla.

Suerte

---

