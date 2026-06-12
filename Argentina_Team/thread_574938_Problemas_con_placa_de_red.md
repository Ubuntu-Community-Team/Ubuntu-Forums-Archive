---
title: "Problemas con placa de red"
date: 2007-10-13
forum: Argentina Team
---

### Post by LolaMora on 2007-10-13
Hola. 
Tuve que llevar mi PC porque palmó la placa madre y por suerte está todavía en garantía.
Resulta que me la cambiaron y me pusieron una mas moderna, por lo que tuvieron que cambiarme el HD.
Estoy queriendo instalar el Feisty desde un LiveCD y lo realiza todo a la perfección, solo que no detecta la placa de red.
En el CD de la placa madre vienen los drivers para linux, pero es muy complicado compilarlos y me da errores de kernel. Según leí por ahi es porque el kernel del LiveCD  es 2.15 y los drivers son para 2.20 (no sé si es verdad, entiendo poco de cosas tan técnicas)
Preciso ayuda, porfi, ya que no puedo actualizar el Feisty recién instalado. 
La motherboard es ASUS P5GC-MX con placa de red incorporada Attansic L2 PCI-E Fast Ethernet
Gracias

---

### Post by Hernán-Amaya on 2007-10-13
mirá Feisty viene con el kernel 2.6.20.  posteá los errores que te tira al complilar así te podremos orientar mejor. Otra opción es esperar una semanita para gutsy

---

### Post by LolaMora on 2007-10-15
Con respecto al Gutsy ya pensé en esa solución.
Te cuento lo que me pasa cuando compilo los drivers:

maria@tux:~$ cd AtL2
maria@tux:~/AtL2$ cd src
maria@tux:~/AtL2/src$ sudo make install
Password:
Makefile:101: *** Linux kernel source not configured - missing config.h.  Alto.
maria@tux:~/AtL2/src$ 

Busoc los Archivos config.h y me muestra estos dos pero están vacíos (0 bytes)
/lib/modules/2.6.20-15-generic/build/include/config/x86/find/smp/config.h
/lib/modules/2.6.20-15-generic/build/include/config/i2o/config.h


¿alguna idea de como sigue?

---

### Post by Hei Ku on 2007-10-15
tenes instalados los headers del kernel? para poder compilar un modulo de kernel, tenes que bajarte el paquete del header correspondiente a tu kernel, y supongo que tambien el source del kernel, dependiendo de como lo compiles.

---

### Post by LolaMora on 2007-10-15
Disculpame, pero no conozco mucho sobre cuestiones técnicas y no sé que está instalado. Te cuento lo que hice.
Por razones de hardware me cambiaron la placa madre y uno de los discos rígidos. A causa de esto perdí el Ubuntu Dapper.
Le instalo el Feisty 64 bits desde un CD live. Se instala todo bien pero no detecta la placa de red por lo que no puedo conectarme para actualizar el SO.
Desde el CD del fabricante Asus copio los drivers y sigo las instrucciones del Readme. Es aqui que me sale lo que puse mas arriba.
Otra cosa, intenté instalar el Gutsy (que sí detecta la placa)  pero se me cuelga después de instalar el paquete Tomboy. Tengo un CD alternate para 64 bits
¿que puedo hacer?    :confused:

---

### Post by Hernán-Amaya on 2007-10-15
para ver que tenes instalado lo mejor usa el synaptic.

por ejemplo si queres ver si tenes los headers en synaptic busca  linux header y ahí te sale 

me imagino que los sources no vienen instalados por omisión así que tendrías que instalarlos, lo podes buscar también con el synaptic busca linux source y ponele instalar y después probá de compilar y si te tira algún error postealo acá

suerte! cualquier cosa pregunta

---

### Post by LolaMora on 2007-10-15
Gracias Hernan
Me fui al Feisty, abri el sinaptic, busqué los paquetes  con nombre:  linux header y me muestra que están instalados.
Te muestro el error que me da en la terminal:

maria@tux:~$ cd AtL2
maria@tux:~/AtL2$ cd src
maria@tux:~/AtL2/src$ sudo make install
Password:
Makefile:101: *** Linux kernel source not configured - missing config.h.  Alto.
maria@tux:~/AtL2/src$

Busqué archivos con el nombre config.h y me mostró lo siguiente:

/usr/src/linux-headers-2.6.20-15/include/acpi/acconfig.h
/usr/share/firefox/chrome/toolkit/content/global/buildconfig.html
/usr/lib/perl/5.8.8/CORE/config.h   [COLOR="SandyBrown"]  #  (este es el único que tiene información)  #[/COLOR]
/usr/src/linux-headers-2.6.20-15-generic/include/config/i2o/config.h [COLOR="sandybrown"]# este está vacío #[/COLOR]
/usr/src/linux-headers-2.6.20-15/debian/Config/config.hp
/usr/src/linux-headers-2.6.20-15/debian/Config/config.hppa
/usr/src/linux-headers-2.6.20-15-generic/scripts/mod/elfconfig.h
/usr/share/doc/libservlet2.3-java/api/javax/servlet/FilterConfig.html
/usr/src/linux-headers-2.6.20-15/include/asm-powerpc/iseries/hv_lp_config.h
/usr/src/linux-headers-2.6.20-15/include/config/ikconfig.h
/usr/src/linux-headers-2.6.20-15/include/net/ipconfig.h
/usr/src/linux-headers-2.6.20-15/kernel/Kconfig.hz
/usr/src/linux-headers-2.6.20-15/include/asm-ia64/sn/klconfig.h
/usr/src/linux-headers-2.6.20-15/include/asm-mips/sn/klconfig.h
/usr/share/doc/libbonoboui2-common/html/libbonoboui-bonobo-ui-engine-config.html
/usr/share/cups/doc-root/help/man-cups-config.html
/usr/src/linux-headers-2.6.20-15/include/config/pci/mmconfig.h
/usr/src/linux-headers-2.6.20-15-generic/include/config/pci/mmconfig.h
/usr/src/linux-headers-2.6.20-15/include/asm-powerpc/pSeries_reconfig.h
/usr/include/python2.5/pyconfig.h
/usr/share/doc/libservlet2.3-java/api/javax/servlet/ServletConfig.html
/usr/src/linux-headers-2.6.20-15/include/linux/tipc_config.h
/usr/src/linux-headers-2.6.20-15-generic/include/linux/tipc_config.h
/usr/lib/perl/5.8.8/CORE/uconfig.h
/usr/share/gtk-doc/html/ximian-connector/ximian-connector-autoconfig.html
/usr/share/gtk-doc/html/ximian-connector/ximian-connector-E2kAutoconfig.html

---

### Post by Hernán-Amaya on 2007-10-15
probá instalando el linux source desde synaptic puede ser que sea eso

---

### Post by LolaMora on 2007-10-15
Efectivamente en el Sinaptic no figuran paquetes linux source.
Lamentablemente no tengo idea de como usar el Sinaptic sin conexión a internet. 
Podría alguien ayudarme con las instrucciones para instalar estos paquetes?
Gracias de antemano.

---

