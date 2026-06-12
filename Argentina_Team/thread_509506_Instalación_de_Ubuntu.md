---
title: "Instalación de Ubuntu"
date: 2007-07-25
forum: Argentina Team
---

### Post by aregnando on 2007-07-25
Hola a todos, quisiera instalar Ubuntu en mi máquina la cual tengo funcionando con XP, la idea sería dejar ese sistema operativo en un disco rígido e instalar Ubuntu en otro disco que le voy a colocar a mi máquina.
La pregunta es como debo configurar este nuevo disco rígido y en el momento de la instalación como hago para que Ubuntu se instale en ese disco en particular.
Muchas gracias.

---

### Post by kowal on 2007-07-26
El instalador es bastante intuitivo.. 

Los discos IDE aparecen como hda, hdb, hdc.. etc.
Los discos SATA aparecen como sda, sdb, sdc, etc.

Cualquier cosa desde el LiveCD tirá un "sudo fdisk -l" para tener una idea de cuales son los discos y particiones.

Más info: [http://www.guia-ubuntu.org/index.php?title=Particionar_el_disco_duro](http://www.guia-ubuntu.org/index.php?title=Particionar_el_disco_duro)

---

### Post by tony_feisty on 2007-07-27
No te hagas problemas, al momento de la instalaciòn te va reconocer todos los discos que tengas, si queres estar mas seguro cuando te pide seleccionar particiones hacelo en forma manual y de ahi seleccionas lo que queres hacer, capacidades, etc....

Saludos.

---

