---
title: "Nuevo en Linux"
date: 2007-07-09
forum: Argentina Team
---

### Post by chiflete on 2007-07-09
Bueno, me presento. Soy Luis y soy nuevo en Linux. Hace poco instale Ubuntu Feisty y la verdad me esta entusiasmando este mundo nuevo de cosas tan accesibles que tiene esta comunidad, y mas que todo me llama la atención lo buenos que son estos foros. Les cuento que desde que instale tuve varios inconvenientes que los solucione a todos y cada uno buscando post de estos foros. Hasta pude hacer andar beryl casi a full con una maquina de hace 5 años :P

Despues de haber solucionado todo esto tengo una pequeña duda que no encuentro en ningun lado y que en verdad es una bobada. Es lo siguiente, tengo 4 particiones del disco, 2 bajo windows y las 2 necesarias de Ubuntu. La cosa es que cuando instale Ubuntu se me crearon dos accesos a las particiones de Windows (sean, sda1 y sda2) en el escritorio de Ubuntu y por mas que busco y busco no encuentro donde sacarlas! Quiero que el desktop quede limpito, solo mi carpeta personal y la carpeta Equipo sin esos dos accesos. 
Ah, es bajo Genome, porque instale KDE y bajo KDE no aparecen. 

Bueno, saludos y voy a estar pasando por aca mas seguido!

---

### Post by njko on 2007-07-09
En el escritorio aparecen todas las unidades montadas al sistema, por ejemplo si conectas una camara digital te va a aparecer, si metes un cd/dvd te va a aparecer. si no queres que te muestre las unidades de windows podes desmontarlas. aunque debe haber un metodo para que no te cree automaticamente un enlace en el escritorio

---

### Post by AnRa on 2007-07-09
Abrí 'gconf-editor' y cambiá la clave '/apps/nautilus/desktop/volumes_visible' a <<false>>. Esto va a hacer que no aparezca ninguna unidad montada.

---

### Post by chiflete on 2007-07-09
Gracias AnRa. Simple y claro. Problema resuelto.

---

### Post by AnRa on 2007-07-10
¡De nada! ;)

---

