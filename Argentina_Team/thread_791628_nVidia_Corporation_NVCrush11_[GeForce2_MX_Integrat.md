---
title: "nVidia Corporation NVCrush11 [GeForce2 MX Integrated Graphics]"
date: 2008-05-12
forum: Argentina Team
---

### Post by prar on 2008-05-12
hola
El problem es bastante comun, he visitado cientos de sitios en ingles y español y no he hallado la solucion.
no encuentro como habilitar mi tarjeta grafica "nVidia Corporation NVCrush11 [GeForce2 MX Integrated Graphics]" y parece que muchos se encuentran en esta situacion de no poder usar a pleno el sistema operativo.
probe de todo, y cuando habilito la tarjeta con compiz-fusion al reiniciar, se cualga despues de iniciar en una pantalla negra y no hay forma tengo que reiniciar pulsar esc, para poder reestablecer el sistema usando la opcion fix.
poniendo
$ lspci
da como resultado
00:00.0 Host bridge: nVidia Corporation nForce CPU bridge (rev b2)
00:00.1 RAM memory: nVidia Corporation nForce 220/420 Memory Controller (rev b2)
00:00.2 RAM memory: nVidia Corporation nForce 220/420 Memory Controller (rev b2)
00:00.3 RAM memory: nVidia Corporation Unknown device 01aa (rev b2)
00:01.0 ISA bridge: nVidia Corporation nForce ISA Bridge (rev c3)
00:01.1 SMBus: nVidia Corporation nForce PCI System Management (rev c1)
00:02.0 USB Controller: nVidia Corporation nForce USB Controller (rev c3)
00:03.0 USB Controller: nVidia Corporation nForce USB Controller (rev c3)
00:04.0 Ethernet controller: nVidia Corporation nForce Ethernet Controller (rev c2)
00:05.0 Multimedia audio controller: nVidia Corporation nForce Audio (rev c2)
00:06.0 Multimedia audio controller: nVidia Corporation nForce Audio (rev c2)
00:08.0 PCI bridge: nVidia Corporation nForce PCI-to-PCI bridge (rev c2)
00:09.0 IDE interface: nVidia Corporation nForce IDE (rev c3)
00:1e.0 PCI bridge: nVidia Corporation nForce AGP to PCI Bridge (rev b2)
01:07.0 Modem: Smart Link Ltd. Unknown device 8800 (rev 02)
02:00.0 VGA compatible controller: nVidia Corporation NVCrush11 [GeForce2 MX Integrated Graphics]
(rev b1)
-----------------------------------------------------------------
pude ver que tipos de dispositivos tengo pero sigo sin hallar la solucion.
alguien sabe como... repito, probe todo y esto es la ultima opcion despues de una semana de busqueda.
no tengo problemas con el audio, pero la resolucion de la pantalla es lo que necesito cambiar ya he modificado exitosamente el xorg.conf pero nada.... se cuelga.
bueno, agradecere su ayuda

---

### Post by faktorqm on 2008-05-12
Hola, instalaste los drivers de la placa de video? Lo tenes que hacer antes de activar compiz-fusion. Si no sabes como instalar los drivers instala el programa "envy" y ese te instala los drivers. Salu2!

---

### Post by prar on 2008-05-12
Active la placa de video, es mas instale envy hice todo, pero me pide reiniciar y cuando lo hago, reinicia dos veces y se cuelga, asi que vuelvo a restaurar desde el inicio. no hay forma. vengo probando desde hace una semana todas las opciones que se dan. estoy pensando si es problema de harware pero me parece que no, con windows lo use a pleno, pero ubuntu 8.04 no la reconoce y cuando lo hace pasa lo que mencione antes, se tilda.

---

### Post by faktorqm on 2008-05-12
Y que driver instalaste? yo tengo una gf4 mx440 y tengo el driver 71.XX y anda bien. o sea, desactiva los efectos, capaz por eso se te cuelga. Si ya instalaste los drivers tambien proba con correr "sudo display-config-gtk" y fijate que este todo en orden. Salu2!

---

