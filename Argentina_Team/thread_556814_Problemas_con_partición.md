---
title: "Problemas con partición"
date: 2007-09-21
forum: Argentina Team
---

### Post by daz! on 2007-09-21
Hola Gente! 

Mi problema es el siguiente: 

Instalé Ubunti Feisty como único SO en una notebook con un disco Sata de 80. Cuando particioné el disco dejé 1gb para swap y quería hacer 2 particiones más. 

Puse / en una de 30 (sda2) y el resto quise dejarlo para almacenar archivos (sda3)

Resulta que cuando hice la partición desde el instalador monté esta última en /media (como creia que tenía en mi PC). :(

El problema es que no monté la partición en /media/sda3 (como tengo en la pc) y ahora toda la carpeta media esta montada en esos 40 y pico gb. :confused:

En resumen. Quiero esa partición poder montarla en mi escritorio (sda3) para almacenar archivos. :confused:

Qué me sugieren??  

Muchas Gracias por su tiempo.

---

### Post by mpbe on 2007-09-22
Tenes que editar el archivo /etc/fstab, busca la linea que monta la particion en /media y agregale el lugar donde queres que la monte /media/sda3 o lo que quieras. Despues crea ese directorio como root.
Reinicias la maquina o haces umount particion y mount /media/sda3 o lo que sea.

Saludos

---

### Post by daz! on 2007-09-23
lMuchas Gracias por tu ayuda. Muy util la info. Problema resuelto

---

