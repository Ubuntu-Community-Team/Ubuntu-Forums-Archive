---
title: "Ati Mobility Radeon 9000 Igp Funciona O No Con Aceleracion 3d?"
date: 2006-12-18
forum: Argentina Team
---

### Post by BlackHero on 2006-12-18
BUENAS TARDESS SEÑORES LA VERDAD CREO QUE ME LEI CASI TODOS LOS HOW TO PARA TRATAR DE HACER ANDAR MI PLAQUITA DE VIDEO TENGO UNA TOSHIBA A80 - SP107 CON UNA PLACA DE VIDEO ATI MOBILITY RADEON 9000 IGP CON 64 MB DDR RAM EXPANDIBLES HASTA 128 EL TEMA ES QUE ME CANSE DE BUSCAR GUIAS Y GUIAS DE PODER HACER ANDAR LA ACELERACION 3D DE ESTA PLACA ME CANSE PROVE DESDE LAS GUIAS DE UBUNTU WIKI HASTA CASI TODAS TODAS LAS VECES ME TIRA ERROR Y HAGO PEDASOS EL XORG.CONF BUENO EL TEMA ES QUIERO CONSULTAR POR QUE BEUNO ME DIJO QUE TIENE LA MISMA PLACA DE VIDEO Y LA INSTALACION POR DEFECTO DE UBUNTU CREO QUE LE INSTALO LOS DRIVERS CORRECTAMENTE AMI ME LOS INSTALA DE TOQUE TAMBIEN UBUNTU PERO CUANDO LARGO ESTO EN COSOLE MIREN LO QUE ME SALE

blackhero@blackhero:~$ glxinfo | grep render
direct rendering: No
OpenGL renderer string: Mesa GLX Indirect

instale diferentes drivers y versiones para poder hacer andar el direct render pero nada cada vez que intento un driver tengo que formatear por el hecho de que nose como solucionar el problema de reacomodar el xorg.conf para volverlo al estado anterior hasta compile el kernel como lo indican las guias para que pueda andar el glx :S ya nose que hacer de ultima pregunta si alguien tiene esta misma placa y que sea capas de instalarla con 3d rendering si no es posible o si sabe que no existe driver alguno para la misma me lo diga la placa es repito ATI MOBILITY RADEON 9000 IGP NO CONFUNDAN CON MOBILITY RADEON 9000 QUE ES DIFERENTE LA MIA IGP VIENE INTEGRADA AL MOTHER CONSUMIENDOLE MEMORIA RAM ESA ES LA DIFERENCIA DESDE YA MUCHAS GRACIAS hasta entre por w3m mediante console al foro para postear pero no pude :P ya formateee desde ya muchas gracias =)

---

### Post by BlackHero on 2006-12-19
al parecer despues de haber provado muchos how tos no eh podido instalar correctamente los drivers de mi placa de video ati mobility radeon 9000 igp al parecer voy a tener que esperar un driver nuevo o cambiar de placa lastima que es una laptop

---

### Post by BOBSONATOR on 2006-12-19
Hola, no hablo espanol mucho, 

Sudo apt-get install xorg-driver-fglrx

y despues

sudo modprobe fglrx

---

### Post by BlackHero on 2006-12-20
yeah i tested too completly but i put ........ | grep render and terminal respondor Mesa drivers :S and direct render: Mesa Indirect all drivers for the ati mobility radeon 9000 IGP not work correctly

---

