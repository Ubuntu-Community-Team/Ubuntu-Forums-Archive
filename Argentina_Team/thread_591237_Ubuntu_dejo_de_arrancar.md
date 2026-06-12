---
title: "Ubuntu dejo de arrancar"
date: 2007-10-25
forum: Argentina Team
---

### Post by Luciano Cossettini on 2007-10-25
Tengo ubuntu 7.04 y djo de arrancar. 
Antes de la pantalla con el logo aparece un mensaje "00000 ACPI unable to locate RSDP". Eso aparecia antes pero igual arrancaba. Pero ahora se queda bastante tiempo en la pantalla con el logo y despues aparece "/bin/sh: cant access tty; job control turned off" y "(initramfs) [316.678347] ata100: exception Emask 0x0 Sact 0x0 Serr ..." y sigue con bastantes mas numeros y letras que para mi son inentendibles. 
Previamente a que deje de responder habia podido solucionar el tema de escribir en particiones NTFS, Pero estaba funcionando bien. 
Otra cosa que habia pasado es que instalé varios programas de sonido y se ve que provocaron un problema porque dejo de haber sonido (no se podia hacer nada relacionado con la placa de sonido, tengo una SB 32 bit).
Agradezco cualquier ayuda...

---

### Post by margori on 2007-10-25
Estimado Luciano:

No soy experto ni mucho menos, pero te puedo decir lo que yo haria en tu caso:

Si ACPI no puede comunicarse con el sistema, deshabilitalo.

Abri el archivo /boot/grub/menu.lst. Modifica la linea de carga del kernel con el modificador acpi=off.

Por ejemplo: 

si dice

kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=f1734898-0578-4878-a831-633465ad5338 ro 

cambialo a

kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=f1734898-0578-4878-a831-633465ad5338 ro acpi=off

Reinicia y fijate que pasa.

---

### Post by Luciano Cossettini on 2007-10-26
El archivo /boot/grub/menu.lst no existe, pero descubri que existe un archivo /boot/initrd.img-2.6.20-15-generic.bak, pero no existe el que no es .bak, por lo cual el acceso directo en el dir raiz esta roto y por eso no debe arrancar. 
El problema es que con el live CD no me da permiso a modificar los archivos. 
Como puedo hacer?

---

### Post by margori on 2007-10-26
> **Luciano Cossettini said:**
> El archivo /boot/grub/menu.lst no existe

Es extraño que no exista este archivo. :(

> **Luciano Cossettini said:**
> El problema es que con el live CD no me da permiso a modificar los archivos. 
Como puedo hacer?

Ciertos archivos tienen pernisos para que solo lo modifique el usuario root. Para modificar un archivo de texto, yo uso este formato:

sudo gedit  [archivo]

Creo que es una forma no segura de abrir un archivo con todos los privilegios, pero me funciona al fin y al cabo.

> **Luciano Cossettini said:**
> , pero descubri que existe un archivo /boot/initrd.img-2.6.20-15-generic.bak, pero no existe el que no es .bak, por lo cual el acceso directo en el dir raiz esta roto y por eso no debe arrancar.

Postea una lista de los archivos que estan en /boot/

He visto una pagina que te recupera el grub, fiajte si te sirve: [http://nand-magazine.net/2006/07/30/recupera-el-grub-que-te-ha-quitado-windows/](http://nand-magazine.net/2006/07/30/recupera-el-grub-que-te-ha-quitado-windows/)

---

### Post by Luciano Cossettini on 2007-10-29
Formatie la particion e instale Ubuntu de vuelta pero aun así dejo de arrancar! Es muy raro porque ya lo habia instalado antes sin problemas. Me pone exactamente lo mismo que antes. Cuando cargo el live CD veo que donde está instalado Ubuntu es en un disco que se llama "volumen 14.4 GB: disk" y que no esta montado, osea que no bootea desde ahí. La ruta a esta particion figura como /dev/hda6 en el editor de particiones, pero cuanro voy al terminal y a grub y pongo "root (hd0,6)" me dice que el disco no existe. ¿que tendria que poner?

---

### Post by margori on 2007-10-29
Deberias poner root (hd0,5)

hda1 = (hd0,0)
hda2 = (hd0,1)
hda3 = (hd0,2)
hda4 = (hd0,3)
hda5 = (hd0,4)
hda6 = (hd0,5)

;)

---

### Post by Luciano Cossettini on 2007-10-30
Pongo en "grub> root (hd0,5)" y me pone "Error 21: Selected disk does not exist". Pero en el editor de particiones me figura como que existe. En fin... se me esta complicando.

---

### Post by sajnox on 2007-10-30
Error 21!!! Yo lo tuve.

Entra en el bios de la maquina y fijate si reconoce bien al disco

En mi caso fue eso

Saludos

---

### Post by Luciano Cossettini on 2007-10-31
Gracias a todos.
 Ya pude solucionar el problema. Estando en (initramfs), que es como una especie de DOS, puse "help" y "exit" y siguió cargando normalmente Ubuntu. Quizá es una tontería pero a mí que soy nuevo nunca se me hibiera ocurrido... Actualicé a Ubuntu 7.10 y ya no me hace ningún problema. En realidad no sé porqué se colgaba en (initramfs)...

---

