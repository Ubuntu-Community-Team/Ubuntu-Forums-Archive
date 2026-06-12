---
title: "Duda al particionar."
date: 2007-06-01
forum: Argentina Team
---

### Post by ricardomanu on 2007-06-01
Hola, tengo la siguiente duda al instalar Ubuntu 7.04, tengo un disco de 80gb, en el cual tiene dos particiones una de 52.1 Gb,la primaria y la secundaria de 22.3 Gb, la primaria tienes windows xp con NTFS y la secundaria tienes fat32, como tengo que hacer para que se instale en la de fat32, tengo que borrar el fat32 y dejarla sin formato.

Gracias.

---

### Post by fetova on 2007-06-01
A la hora de acomodar las particiones (no recuerdo que paso), ponle editar manualmente las particiones, despues aparecen tus particiones, borras la fat32, pones una particion Linux/swap de el doble de tamaño de tu memoria ram al final del disco y le das el resto de espacio a tu particion ext3 para ubuntu al la cual le vas a poner como punto de montaje "/"

Cualquier duda avisas :)

---

