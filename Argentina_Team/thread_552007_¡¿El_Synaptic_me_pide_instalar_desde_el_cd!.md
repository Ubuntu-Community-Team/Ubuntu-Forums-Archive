---
title: "¡¿El Synaptic me pide instalar desde el cd?!"
date: 2007-09-15
forum: Argentina Team
---

### Post by Kittukahier on 2007-09-15
Yo instalé ubuntu FF 704 alternate desde una imágen del cd, copiado al disco duro, siguiendo el tutorial en ingés "Installing/From Windows", y me ha resultado perfecta.
Ahora me encuentro que para agregar paquetes me pide el cd, cuando quiero instalar paquetes desde el synaptic y desde Terminal. 
¿Alguna idea, alguien?

---

### Post by Montsegur87 on 2007-09-15
debes tener el cd en la lista de repositorios. Un repositorio de paquetes puede estar en un servidor en internet , en un CD o en un servidor de intranet.

Fijate en repositories del Synaptic , la 2da solapa si mal no recuerdo , de sacar el cd ese.

---

### Post by FlyerDie on 2007-09-15
fijate desde donde esta tomando las source lists en:

/etc/apt/sources.list

seguramente tengas apuntando al cdrom por el metodo de instalacion que usaste...:confused::confused:

Si en la sources.list tenes el cdrom o no tenes nada, avisa que te paso la que tengo yo.

:guitar:

---

### Post by Kittukahier on 2007-09-16
Muchisimas gracias por responder.
Hice lo siguiente, observé que ubuntu tiene una carpeta que se llama cdrom, primero: a lo bruto, puse la iso ahí, hice andar synaptic y no pasó nada, seguido busqué un programa que montara cd dvd virtuales (encontré el AcetoneISO pero no me convencí de seguir bajando paquetes). Buscando entonces, di con la página (puesta en 2005) que hablaba de deamon tools para W, que ya lo conocía y al principio comenta que en linux no hacía falta tal cosa porque estaba la susodicha carpeta y daba el siguiente command:

    mount -o loop /path/to/file.iso /path/to/mount/point

yo puse algo así:

$ sudo mount -o loop /home/"carpeta-personal"/ubuntu.iso /cdrom

todo el contenido del hizo quedó ahí, y pasé a probar instalar y entonces sucedió que arrancó.
Despues probé con una imagen .nrg de una película en dvd, también me fijé como quedó la carpeta y se encontraban las carpetas de dvd de audio y video, salí. Paso seguido hice secundario en la carpeta y elegí reproducir con otra aplicación y ahí elegí totem para probar, y se reprodujo el dvd...
¿qué les parece?

---

### Post by FlyerDie on 2007-09-16
esta bien, pero esa es una solucion para "el momento" ya que nunca te vas a enterar si hay upgrades/updates de paquetes, ya que no tenes repositorios para que chequeen...salvo el CDROM.

Fijate lo que te pusimos mas arriba, de esa manera vas a poder mantenerte actualizado ;)

---

### Post by Kittukahier on 2007-09-16
Si ya fuí al source.list tiene varias "dev http:..." 
No dice nada de cdrom sólo. Lo extraño fue que para dos miseras cosas me pidió el cdrom el resto que vengo instalando lo toma de red super bien. Después de la instalación inicial hizo una actualización de 120 o más paquetes por eso me llamó la atención y tuve que buscar ayuda.
Desde ya Muchisimas gracias por responderme.

---

### Post by jpmorelli on 2007-09-16
Lo que hiciste es correcto, para montar ISO's como unidades virtuales el comando es el que encontraste:

sudo mount archivo.iso  /media/iso/ -t iso9660 -o loop


Que te pida el CD de Ubuntu 7.04 FF es normal de acuerdo al paquete que hayas seleccionado para instalar. El instalador de paquetes busca desde donde puede bajar los archivos, luego selecciona los medios y examina cual es la versión más nueva y luego selecciona cual es la mejor fuente desde donde bajarla, obviamente si el archivo se encuentra tanto en repositorio externo como en el CD-Rom y ambos son las mismas versiones, elije por defecto la del CD ya que es más rápida y segura ( y barata ). 
Si no querés que te vuelva a pedir el CD solo tenes que deshabilitar el CD Rom desde la lista de repositorios. En el modo gráfico se saca la selección del CD en las opciones de los repositorios y desde consola editás el archivo /etc/apt/source.list y le ponés un símbolo "#" delante de la línea que tiene el CD-Rom.
Suerte !

---

