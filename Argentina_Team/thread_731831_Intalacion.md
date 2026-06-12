---
title: "Intalacion"
date: 2008-03-22
forum: Argentina Team
---

### Post by ghertzan on 2008-03-22
Buenas
Logre instalarlo!
Pero en el inicio no me muestra la opcion de Windows XP para iniciar, la compu la uso yo y mi novia, Diganme porfa como hago para que se pueda bootear con WinXP tambien.
Me van a matar si no puedo!

Gracias!

---

### Post by Apokalyptica79 on 2008-03-22
Hola encontré un enlace a ver si te sirve:
[http://www.sorgonet.com/linux/grubrestore/]("http://www.sorgonet.com/linux/grubrestore/")
Saludos

---

### Post by ghertzan on 2008-03-22
Gracias,
Pero no es mi caso.
Lo tengo instalado en discos diferentes, Windows en un SATA y Linux en el comun, pienso que eso debe ser problema.

Gracias de todos modos!

---

### Post by llove on 2008-03-22
hola, fijate si te resulta mas facil con algun herramienta grafica para editar grub, pero igualmente te tendria que servir lo que te pasaron antes, sino, antes de booter, elegi con que disco queres hacerlo.

[http://cactusdigital.net/2007/12/27/qgrubeditor-editor-grafico-grub/](http://cactusdigital.net/2007/12/27/qgrubeditor-editor-grafico-grub/)

espero que te sirva, saludos.

---

### Post by gmunioz on 2008-03-22
Hola ghe...:
Pulsa:
Aplicaciones > Accesorios > Terminal
Se abrirá una consola.
Escribe:
sudo fdisk -l
Copia la salida y pégala en el post.
Escribe gedit /boot/grub/menu.lst
Se abrirá un archivo.
Copia todo su contenido y pégalo tambien en el post.
Saludos.

---

### Post by Mafber on 2008-03-23
Una pregunta: vos cambiaste la secuencia de booteo de la mother? te pregunto porque yo tambien tengo instalado ubuntu y windows en dos discos, y dependiendo de que disco bootear me sale ubuntu o windows. Controlá en el setup, cual es el disco del cual estas bootiando. Me parece, por los datos que das, que tenes que tener como disco de booteo al ata ("común") y no al sata.

Otra pregunta: cuando bootea y te muestra el menú (grub) que dice 
----------------------------------
Ubuntu, kernel.....
Ubuntu, kernel.....(recovery mode)
...
...
otro sistema operativo:
microsoft windows
-----------------------------------
esa ultima opción te debería llevar a windows

una ultima pregunta: (no quiero preocuparte) estas seguro que instalaste en el "común" y no en el sata????????

---

### Post by ghertzan on 2008-03-23
Gracias Gente son lo mas, ya lo resolvi!
Son lo mejor!!!! 
Saben que sigo teniendo problemas con flash, y tambien con algunos programas como celestia por ejemplo, lo ejecuto y cuando se empieza a cargar se clava mal, que ni el mouse se mueve, esto tambien me pasa cuando estoy navegando, primero pense que era el mozilla asi que instale epiphany pero me pasa lo mesmo...
Ya estoy empezando a pensar que mi hard no es compatible... Es un bajon por que tengo que reiniciar de a ratos.

Saludos!!!!

---

