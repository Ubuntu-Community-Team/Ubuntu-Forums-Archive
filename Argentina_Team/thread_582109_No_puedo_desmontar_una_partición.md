---
title: "No puedo desmontar una partición"
date: 2007-10-19
forum: Argentina Team
---

### Post by Luciano Cossettini on 2007-10-19
Instalé Ubuntu ayer, y me reconoció una particion y un disco rígido que tenia en formato ntfs, pero no me deja escribir en ellos. Investigué y me bajé la herramienta ntfs-3g, la pude instalar. Hasta ahí todo bien. Pero no me deja desmontar los volúmenes para re-montarlos, me dice: "no se puede desmontar el volumen" Detalles: "unmount: montaje de /media/hda5 no concuerda con fstab". Con el otro volumen me dice lo mismo (pero con el otro nombre: /media/hdb1). Entré a editar fstab, pero no entendí bien cual es el problema así que no quise tocar nada. 
Por favor, agradezco cualquer ayuda... gracias

---

### Post by Hernán-Amaya on 2007-10-19
manda el fstab así vemos que pasa, que versión de ubuntu tenes??

---

### Post by tzulberti on 2007-10-19
Creo que como te las monta automaticamente, para desmontarlas tenes que usar sudo antes del umount.

---

### Post by Luciano Cossettini on 2007-10-20
hice quilombo con la salida de TV y la pantalla y tuve que reinstalar (ubuntu 7.04). Pero esta vez no me detectó automáticamente las particiones(?). Voy a bajar de vuelta la herramienta ntfs-3g y tratar de montarlas con ella.

---

### Post by tzulberti on 2007-10-20
Fijate si las mismas te aparecen en el archivo /proc/partitions.

---

### Post by Luciano Cossettini on 2007-10-22
No figuran en  /proc/partitions. Figuran ambas como carpetas en el directorio raíz del sistema de archivos (?) y como volúmenes no montados, las dos cosas al mismo tiempo. Cuando quiero acceder a estas particiones las monta pero sólo como lectura. Las trato de montar con ntfs-3g pero no puedo, ya me lei como 5 tutorials y todos dicen cosas diferentes. 
Instale la herramienta mediante # sudo apt-get install ntfs-3g (previamente la bajé) Aparentemente se instaló bien.
 Modifiqué # gksu gedit /etc/fstab
Pero cuando  pongo # sudo mount -a me dice "mount: el punto de montaje ntfs-3g no existe".
O sea hay algo que está mal...
Adjunto el archivo fstab.

---

### Post by Hei Ku on 2007-10-22
te falta el punto de montaje, la carpeta donde queres que ponga esos discos, como /media/hda1 o algo asi.

Si te fijas en la entrada del ext3, tenes la UUID (identificador del disco) y a continuacion "/" que es la carpeta raiz. Eso quiere decir que ese disco se monta como raiz. Para los otros tenes que montarlos en otra carpeta, gralmente en /media/algo.

---

### Post by Luciano Cossettini on 2007-10-25
Ya pude solucionar el tema de las particiones NTFS, pude acceder y escribir en ellas. Gracias a todos. 
Ahora tengo un problema mas grave, jeje,  pero lo posteo por separado porque es muy distinto.

---

### Post by facundocorradini on 2007-10-25
Recomendación sencilla, ya que veo que acabas de reinstalar: instala Gutsy, que ya trae integrado el soporte para escribir en NTFS

---

