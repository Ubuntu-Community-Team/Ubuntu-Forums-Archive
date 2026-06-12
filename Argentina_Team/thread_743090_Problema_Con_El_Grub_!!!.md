---
title: "Problema Con El Grub !!!"
date: 2008-04-02
forum: Argentina Team
---

### Post by leonardo83 on 2008-04-02
Buenas gente, no se si se acuerdan pero habia borrado Ubuntu de mi compu.
Bue cuestion que me encabrone MAL con Winchor por cosas que pasaron en la semana y decidi instalar Ubuntu 7.10 de nuevo.
Como seguro no se acuerdan, tengo un rigido de 60 gb con WinME y otro rigido de 80 dinde poner ubuntu :P
Bue, cuestion que uso el live cd, lo pruebo, me conecte a internet por placa (no lo podia creer y ni siquiera tenia instalado el SO !!!) y me encanto.
Pase a instalarlo, 20 o 30 minutos despues ya estaba instalado y me pedia reiniciar, reinicio, saco el cd, carga el sistema y me aparece error del Grub, por lo que me fije dice Grub error , Error 18 ....
y se queda ahi, lo reinicie, me fije desde el boot s estaba todo ok, error 18... y no pasa nada! :confused:
asi que lamentablemente agarre el diskette de inicio de winme y aplique fdisk/mbr y ahora arranca joya...pero Winchor.
No se si quedo granado el ubuntu en el otro rigido pero ahora no em aparece mas el grub. Tengo que instalarlo de nuevo? saben como se soluciona ese error , o que deberia hacer? lo instale siguiendo loas pasos del cd, y es mas, no hice ninguna particion, como dije use completamente el segundo rigido (o hdb) y salio todo bien.
Espero poder usar ubuntu pronto asi que espero me respondan para ver donde esta el error, vi post similares pero con error 22 u otras cosas, no se que tengo que hacer. :(
Desde ya gracias, un saludo.

---

### Post by mcongom on 2008-04-02
fijate [aca]("http://santib90.wordpress.com/2007/11/05/recuperar-un-arranque-dual-ubuntu-windows/") que por ahi te sirve.
Saludos

---

### Post by leonardo83 on 2008-04-02
gracias man!!! :)
voy a probar eso a ver si levanta y si es asi posteo como solved, y sino me van a leer aca de nuevo.

Gracias gente!!! (Y)

---

### Post by gmunioz on 2008-04-02
Hola leo...:
Es posible que exista alguna incompatibilidad entre tu bios, el Grub y tus discos.
En general, cuando aparece el error 18 del Grub imputable a: 18 : Selected cylinder exceeds maximum supported by BIOS, es decir que una lectura intenta ir más allá del área direccionada por el BIOS, es conveniente instalar Ubuntu con particionamiento manual, creando una partición primaria, activa, en formato ext3 de unos 384 megas al comienzo del disco, para /boot, esto no solo evita el error sino que de borrarse Ubuntu, al mantenerse /boot no habrá error del Grub paralizando el sistema.
Por eso siempre acostumbro a instalar Ubuntu en:
Una partición primaria, activa, ext3, de 384 megas para /boot
Una lógica reiserfs de la menos 8 gigas para /
Una lógica de intercambio de no más de 768 megas para swap
Una lógica reiserfs de todo lo que tenga disponible para /home
Saludos.

---

### Post by leonardo83 on 2008-04-03
> **gmunioz said:**
> Hola leo...:
Es posible que exista alguna incompatibilidad entre tu bios, el Grub y tus discos.
En general, cuando aparece el error 18 del Grub imputable a: 18 : Selected cylinder exceeds maximum supported by BIOS, es decir que una lectura intenta ir más allá del área direccionada por el BIOS, es conveniente instalar Ubuntu con particionamiento manual, creando una partición primaria, activa, en formato ext3 de unos 384 megas al comienzo del disco, para /boot, esto no solo evita el error sino que de borrarse Ubuntu, al mantenerse /boot no habrá error del Grub paralizando el sistema.
Por eso siempre acostumbro a instalar Ubuntu en:
Una partición primaria, activa, ext3, de 384 megas para /boot
Una lógica reiserfs de la menos 8 gigas para /
Una lógica de intercambio de no más de 768 megas para swap
Una lógica reiserfs de todo lo que tenga disponible para /home
Saludos.


Cla. Bue decime como eligo toooood eso porque para instalar solo tengo como opcion el disco esclavo que es el de 80, que esta (o estaba) vacio.
No se como hacer tantas particiones desde la instalacion.
Un abrazo, estoy probando eso del live cd y el grub... :(

---

### Post by leonardo83 on 2008-04-03
bue  no se que pasa pero ahora tampoco me lee el live cd, como lo hacia antes cuando tuve este problema AAAAAARRRRRRGGGGHHHH!!


parece que mi unica solucion sera comprarme otra pc, maldicion, ya me esta cansando esto.:mad::mad::mad::mad:
Iguakmente gracias por los datos, voy a ver que pasa.Saludos


PD: no tengo plata para una pc nueva :(

---

