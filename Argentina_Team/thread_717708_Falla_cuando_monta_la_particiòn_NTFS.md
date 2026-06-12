---
title: "Falla cuando monta la particiòn NTFS"
date: 2008-03-07
forum: Argentina Team
---

### Post by tony_feisty on 2008-03-07
Un saludo para todos,

Mi problema es el siguiente, no sè porque cuando inicio a veces monta bien la particiòn y en otras ocasiones me tira un error HAL-STORAGE-FIXED-MOUNT-ALL-OPTIONS REFUSED UID 1000, y no me deja ingresar a la particiòn NTFS... tengo que estar montandola en forma manual... de tres veces que inicio, dos monta mal la particiòn... 

Si alguien tiene idea, estuve buscando y aparentemente es un tema de permisos pero no sè como solucionarlo... 

Gracias, y un abrazo a todos.

---

### Post by Radiobuzz on 2008-03-07
Estuve buscando información y según parece, es suficiente conque instales ntfs-config (desde apt-get), luego lo abrís y seleccionás la opción de lectura y escritura para discos extraibles. Ojalá te sirva.

---

### Post by gmunioz on 2008-03-08
Hola ton...:
Prueba lo siguiente:
Instala ntfs-3g libfuse2 fuse-utils ntfsconfig
Terminada la instalación, si esta montada la partición desmontala.
Pulsa:
Aplicaciones > Herramientas del sistema > herramienta de configuración NTFS > activa para dispositivos internos y externos > cierra
ya tendría que estar siempre montada al inicio la partición ntfs.
Saludos.

---

### Post by tony_feisty on 2008-03-17
Antetodo un saludo, instale ntfs-conf que era el que me faltaba, al tildar las opciones de montar unidades int-ext, me tira un error, que no se ha podido montar /media/hda1 y que el punto de montaje no existe.  ¿?¿?¿?

Gracias

---

### Post by tony_feisty on 2008-03-17
Agrego info, mi fstab

proc /proc proc defaults 0 0
# Entry for /dev/hda2 :
UUID=b26ef609-5a51-46b8-ab10-3a502c3d575c / ext3 nouser,defaults,errors=remount$
/media/hda1 ntfs defaults,umask=007,loop,uid=0,gid=0,auto,rw,users,quiet 0 1 0
# Entry for /dev/hda3 :
UUID=5FEB-4959 /media/hda3 vfat defaults,utf8,umask=007,uid=0,gid=46,auto,rw,no$
# Entry for /dev/hda4 :
UUID=6ee4b03a-8cbe-45fd-a6da-41dc8e6eb2bb none swap sw 0 0
/dev/hdc /media/cdrom0 udf,iso9660 user,atime,noauto,rw,dev,exec,suid 0 0
/dev/fd0 /media/floppy0 auto user,atime,noauto,rw,dev,exec,suid 0 0
/dev/hda1 /media/hda1 ntfs-3g defaults,locale=es_AR.UTF-8 0 0

---

### Post by kha0s101 on 2008-03-18
[COLOR="DarkGreen"]Hola.

Es una nimiedad quizás, pero has entrado a windows y ejecutado "chkdsk /f"? el ntfs tiene unos descriptores de medios que al parecer son bastante sensibles" y por lo general, cuando hay falla en el montaje, es que alguno de ellos indica alguna clase de error, por lo tanto Ubuntu no monta la partición automáticamente.

Chkdsk /f comprueba y corrige esa situación y vuelve a comprobar en el próximo inicio de windows. Si hasta ahí anduvo todo bien, en Ubuntu deberías poder montar sin problemas las particiones ntfs. 

Espero que soluciones tu problema y sea solo eso. Acabo de darme de narices con un rosario de sectores defectuosos así que estoy en eso. 

Saludos y suerte.

[/COLOR]

---

### Post by Tosh78 on 2008-03-18
Hey, yo instale el ntfs-config tambien hace unos dias. Ese error me lo tiraba porque yo le estaba poniendo una ubicacion, y en realidad tenia que ponerle el nombre con el que queria que apareciera montada la particion ntfs. O sea...yo le estaba poniendo /media/wingarch y en realidad le tenia que poner solo wingarch o miparticion_ntfs.
De todas formas, te cuento que despues de instalar ntfs-config tuve problemas para apagar, es decir cuando le das al boton de apagar, no apaga. Ojala que no sea tu caso.

---

### Post by tony_feisty on 2008-03-20
Es una risa, antes si bien me mostraba el "nombre" de la partición NTFS tenia que montarla manualmente, despues de hacer chkdsk (no tiro ningún error) ni me muestra la partición, ni me deja montarla, para linux creo que ni existe, me parece que tiro la toalla, me gano por cansancio... jajaja... 

Saludos...

PD: Si hay alguien que le quede alguna chispa, porque ya no sé que probar.
PD2: Lo que reconozco es que debe haber algo raro de la partición NTFS que el piojoso Windows no me muestra error y linux me lo rebota... pero anda saber que... tanto Windows como linux los instale de cero, tal vez tendria que borrar con algún programa tipo partition magic para estar seguro que el disco quede limpio, pero seria otro tema que me llavaria mas tiempo y lo mejor sería no llegar a eso y solucionarlo con que lo reconozca...

---

### Post by Hei Ku on 2008-03-21
probaste el gparted, a ver q te dice?

---

### Post by chango08 on 2008-05-01
gmunioz gracias por la data, me sirvio de 10 :) !   saludos

---

### Post by sajnox on 2008-05-01
> que no se ha podido montar /media/hda1 y que el punto de montaje no existe. ¿?¿?¿?

Entra en la carpeta /media y fijate si existe la carpeta hda1, en caso que no exista

```
sudo mkdir /media/hda1

```

Te dice que la carpeta donde lo queres montar al disco no existe

---

