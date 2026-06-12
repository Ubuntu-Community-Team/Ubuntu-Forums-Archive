---
title: "Grub con ubuntu en sata y xp en ide"
date: 2007-08-14
forum: Argentina Team
---

### Post by .NicK_LoVe on 2007-08-14
Hola gente, mi problema es el siguiente: instale ubuntu en un sata de 160gb el cual me aparece en grub como hd0; luego conecte un disco ide con xp (hd1).

El tema es q despues de probar varias veces con grub logre q todo me funcione, pero cada vez q inicio xp me queda el bios con el disco ide como hd0.

Mi grub es el siguinte:


title		Windows Xp Professional
rootnoverify		(hd1,1)  -----------> no entiendo porque no funciona como (hd1,0)
savedefault
makeactive
chainloader	+1
map	(hd0) (hd1)
map	(hd1) (hd0)


title		Ubuntu, kernel 2.6.20-16-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=4251d256-36b9-45c9-a52e-ba28d8729c39 ro quiet splash locale=es_ES
initrd		/boot/initrd.img-2.6.20-16-generic
quiet
savedefault

cada vez q inicio xp tengo q entrar en el bios y poner el sata como hd0.

Espero q me puedan ayudar.

---

### Post by Mafber on 2007-08-15
Hola NicK_LoVe!! te cuento como solucioné el problema que planteas.
Cuando prendo mi pc toco F11 (esto es para mi mother MSI, fijate como es en la tuya) y me sale un menú chiquito que me da las opciones para elegir de donde arrancar (muestra los distintos discos, las unidades opticás, etc). De este modo no tengo que cambiar la bios. Por tanto cuando reinicio, vuelve a bootear de la manera que estaba definido en la bios (y xp no se vuelve loco).
Suerte!!!! :)

---

### Post by .NicK_LoVe on 2007-08-16
Mafber tenes toda la razón!!!!!!!!!, yo tengo una MSI tambien y usaba esta opción para los LiveCD.

Muchisimas gracias!!!!!!!!!!!

---

