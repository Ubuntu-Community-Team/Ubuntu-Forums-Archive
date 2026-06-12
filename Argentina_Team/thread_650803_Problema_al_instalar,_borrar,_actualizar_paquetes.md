---
title: "Problema al instalar, borrar, actualizar paquetes"
date: 2007-12-26
forum: Argentina Team
---

### Post by Thalskarth on 2007-12-26
Bueno mi problema es asi...

Hace ya mas de una semana, instalé el VMware player para poder usar una maquina virtual... que finalmente no me gusto y lo temriné cambiando por el VirtualBox.

pero desde que sintale ese Vmware player, ahora siempre que instalo, borro, actualizo algun programa (sin importar si es con aptitude, Synaptic, Apt-get o el que sea) me sale un mensaje diciendo "Los siguientes paquetes parcialmente instalados serán configurados: linux-image-2.6.22-14-generic" y se "tilda durante unos 30 segundo" para que eal final simepre salga el cartel de de quedbo reiniciar el ubuntu.

Aca les dejo la transcripion completa para que vean lo que digo. (Ahi estoy instalando el rar como ejemplo):

> thalskarth@thalskarth-desktop:~$ sudo aptitude install rar
Leyendo lista de paquetes... Hecho
Creando árbol de dependencias       
Leyendo la información de estado... Hecho
Leyendo la información de estado extendido       
Inicializando el estado de los paquetes... Hecho
Construir la base de datos de etiquetas... Hecho
Se instalarán los siguiente paquetes NUEVOS:
  rar 
Los siguientes paquetes parcialmente instalados serán configurados:
  linux-image-2.6.22-14-generic 
0 paquetes actualizados, 1 nuevos instalados, 0 para eliminar y 0 sin actualizar.
Necesito descargar 506kB de ficheros. Después de desempaquetar se usarán 1036kB.
Escribiendo información de estado extendido... Hecho
Des:1 [http://ar.archive.ubuntu.com](http://ar.archive.ubuntu.com) gutsy/multiverse rar 1:3.7b1-2 [506kB]
Descargados 506kB en 3s (135kB/s).                    
Seleccionando el paquete rar previamente no seleccionado.
(Leyendo la base de datos ...  
114633 ficheros y directorios instalados actualmente.)
Desempaquetando rar (de .../rar_1%3a3.7b1-2_i386.deb) ...
Configurando linux-image-2.6.22-14-generic (2.6.22-14.47) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.22-14-generic
Not updating initrd symbolic links since we are being updated/reinstalled 
(2.6.22-14.46 was configured last, according to dpkg)
Not updating image symbolic links since we are being updated/reinstalled 
(2.6.22-14.46 was configured last, according to dpkg)
Running postinst hook script /sbin/update-grub.
[: 25: ==: unexpected operator
exec: 25: -a: not found
User postinst hook script [/sbin/update-grub] exited with value 2
dpkg: error al procesar linux-image-2.6.22-14-generic (--configure):
 el subproceso post-installation script devolvió el código de salida de error 2
Configurando rar (1:3.7b1-2) ...
Se encontraron errores al procesar:
 linux-image-2.6.22-14-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)
Un paquete no se pudo instalar. Intentado recuperarse:
Configurando linux-image-2.6.22-14-generic (2.6.22-14.47) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.22-14-generic
Not updating initrd symbolic links since we are being updated/reinstalled 
(2.6.22-14.46 was configured last, according to dpkg)
Not updating image symbolic links since we are being updated/reinstalled 
(2.6.22-14.46 was configured last, according to dpkg)
Running postinst hook script /sbin/update-grub.
[: 25: ==: unexpected operator
exec: 25: -a: not found
User postinst hook script [/sbin/update-grub] exited with value 2
dpkg: error al procesar linux-image-2.6.22-14-generic (--configure):
 el subproceso post-installation script devolvió el código de salida de error 2
Se encontraron errores al procesar:
 linux-image-2.6.22-14-generic
Leyendo lista de paquetes... Hecho                   
Creando árbol de dependencias       
Leyendo la información de estado... Hecho
Leyendo la información de estado extendido      
Inicializando el estado de los paquetes... Hecho
Escribiendo información de estado extendido... Hecho
Construir la base de datos de etiquetas... Hecho     
thalskarth@thalskarth-desktop:~$ 


Como puedo hacer para solucionar este problema???

Desde ya, muchas gracias

---

### Post by vk-cdg on 2007-12-27
Si buscás el paquete en el synaptic te aparece marcado de alguna manera? (para instalar, para reinstalar o para desinstalar)

A mi me paso hace unas semanas, que quise instalar un paquete que dio error pero me quedó marcado en el synaptic, a partir de ahí, cada vez que le daba "aplicar" a alguna instalación, me intentaba instalar ese paquete y daba error. Luego de 2 horas me di cuenta (cuando finalmente leí el mensaje)

---

### Post by Thalskarth on 2007-12-27
> **vk-cdg said:**
> Si buscás el paquete en el synaptic te aparece marcado de alguna manera? (para instalar, para reinstalar o para desinstalar)

A mi me paso hace unas semanas, que quise instalar un paquete que dio error pero me quedó marcado en el synaptic, a partir de ahí, cada vez que le daba "aplicar" a alguna instalación, me intentaba instalar ese paquete y daba error. Luego de 2 horas me di cuenta (cuando finalmente leí el mensaje)

ese paquete de linux-image-etcetcetc me aparece como "instalado" en synaptic. que deberia hacer entonces???

Pd: no se mucho del tema, pero ese no es parte el kernel o algo asi?

---

### Post by vk-cdg on 2007-12-28
Probá marcarlo para reinstalar a ver que pasa.

---

### Post by kowal on 2007-12-28
Parece un problema con los modulos de VMware (vmnet y vmmon). Como instalaste VMware Player? (En Ubuntu Gutsy solamente se puede instalar VMware Server y no el Player desde apt). Intentaste desinstalar VMware player?

---

### Post by Thalskarth on 2007-12-28
> **vk-cdg said:**
> Probá marcarlo para reinstalar a ver que pasa.
No paso nada... siguwe igual todo

> **kowal said:**
> Parece un problema con los modulos de VMware (vmnet y vmmon). Como instalaste VMware Player? (En Ubuntu Gutsy solamente se puede instalar VMware Server y no el Player desde apt). Intentaste desinstalar VMware player?
Lo hice con el tutotial de esta pagina: [http://www.openside.com.ar/wordpress/?p=145](http://www.openside.com.ar/wordpress/?p=145)

usando este repositorio para gutsy (que es mi version): deb [http://ppa.launchpad.net/cschieli/ubuntu](http://ppa.launchpad.net/cschieli/ubuntu) gutsy main restricted.

Es más, en si no se si el problema "nacio" al instalar el VMware player o al desinstalarlo... ya que en el interin de instalart desisntalar no use el apt para nada.

y recien, despues de desintalarlo empeze a notar este problema

---

### Post by jpmorelli on 2007-12-29
Yo una vez tuve un problema similar con unos paquetes que dependían de otros y que a su vez dependían de los anteriores por ende no se podían instalar. Luego de varias pruebas, fuí a Synaptic marqué los paquetes rotos y directamente puse que los elimine totalmente, a partir de ahí se arregló.

---

### Post by Thalskarth on 2007-12-29
> **jmorelli said:**
> Yo una vez tuve un problema similar con unos paquetes que dependían de otros y que a su vez dependían de los anteriores por ende no se podían instalar. Luego de varias pruebas, fuí a Synaptic marqué los paquetes rotos y directamente puse que los elimine totalmente, a partir de ahí se arregló.

Tengo miedo de borrarlos completamente, porque en si... el linux-imgae-generic no es parte el kernel???

Si lo borro, me pide reiciniciar... es seguro hacerlo?? o me quedo sin poder arrancarla luego???

---

### Post by Hei Ku on 2007-12-29
y... por las dudas fijate que puedas volver al kernel anterior. proba de reiniciar con la imagen de kernel anterior antes de probar desinstalar el actual.

es algo jodido, yo probaria de hacerlo todo sin reiniciar.

---

### Post by Thalskarth on 2007-12-29
> **Hei Ku said:**
> y... por las dudas fijate que puedas volver al kernel anterior. proba de reiniciar con la imagen de kernel anterior antes de probar desinstalar el actual.

es algo jodido, yo probaria de hacerlo todo sin reiniciar.

ahhh... entonces entoy en problemas... porque no se como hacer esas cosas...

vere de buscar en google algo de info sobre ese tema antes de tocar nada

---

### Post by jclevien on 2007-12-29
Hola Thalskarth,

Mirando un poco el stack de llamadas que posteaste, observo que el shell script que falló es el /sbin/update-grub.

Como dice ahí, fijate la línea 25 a ver cual es el error. Me huele a que falte alguna doble comilla...


Jaja... olí bien! :) Encontré este thread que tiene la solución:
[http://ubuntuforums.org/archive/index.php/t-595008.html](http://ubuntuforums.org/archive/index.php/t-595008.html)


Gracias. Saludos.


Juan

---

### Post by Thalskarth on 2007-12-29
> **jclevien said:**
> Hola Thalskarth,

Mirando un poco el stack de llamadas que posteaste, observo que el shell script que falló es el /sbin/update-grub.

Como dice ahí, fijate la línea 25 a ver cual es el error. Me huele a que falte alguna doble comilla...


Jaja... olí bien! :) Encontré este thread que tiene la solución:
[http://ubuntuforums.org/archive/index.php/t-595008.html](http://ubuntuforums.org/archive/index.php/t-595008.html)


Gracias. Saludos.


Juan

Gracias por el dato... pude repararlo... se ve que era eso :)

gracias

---

### Post by jpmorelli on 2007-12-30
MIrá, nunca me pasó de desisntalar algún paquete y que Ubuntu se tornara no iniciable si necesita reiniciar. Igualmente yo haría lo que dice Hei Ku , aunque me pida reiniciar seguiría con la desinstalación/instalación y vería que pasa.

---

