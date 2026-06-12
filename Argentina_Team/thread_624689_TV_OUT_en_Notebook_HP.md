---
title: "TV OUT en Notebook HP"
date: 2007-11-27
forum: Argentina Team
---

### Post by Oktubre on 2007-11-27
Buenas, 

tengo una notebook hp 1325 la con Ubuntu 7.10. Cuando quiero mandar la salida de vidio al TV se me freeza la pantalla (se ve como mal la resolucion, con rayitas y muchas veces lo mismo) y no se ve nada en la TV.

A alguien le sucedio lo mismo? Alguna idea? 

Gracias, 

Salduos,

---

### Post by Hernán-Amaya on 2007-11-27
que placa de video tenes? como tenes seteado el segundo monitor?

saludos ricoteros!!

---

### Post by Oktubre on 2007-11-27
Gracias Hernan!

En el xorg.conf tengo lo siguiente: 

[I]Section "Device"
	Identifier	"Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller"
	Driver		"i810"
	BusID		"PCI:0:2:0"
EndSection[/I]

Saludos,

---

