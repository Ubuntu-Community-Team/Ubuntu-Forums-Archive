---
title: "Instalar Ubuntu Exo Nifty"
date: 2014-12-15
forum: Argentina Team
---

### Post by Maximiliano_Garc on 2014-12-15
Hola Gente,

Estoy necesitando instalar Ubuntu en una Exo Nifty, empecé por crear un USB Booteable y desde el vamos no te me reconoce el touchpad. Alguien sabe como solucionarlo?

Agradecería si alguien que tenga andando al 100% Ultrabook de esta empresa me diera una mano!

Saludos,

MG

---

### Post by pabloab7772 on 2015-04-15
Acabo de ver [esta solución en la lista Ubuntu-ar]("https://lists.ubuntu.com/archives/ubuntu-ar/2013-September/047578.html"). Por las dudas cito:
> 
Primero, el touchpad se solucionó con la opción que me pasaste, para hacer las cosas mas fáciles edite el archivo /boot/grub/grub.cfg y a la linea del sistema operativo le añadi el i8042.noloop=1 con esto también funciona el multitouch.
Al intentar instalarlo, el instalador de ubuntu no me reconocía el disco, pero el gparted si lo reconoce.
Para poder instalarlo buen tuve que hacer 2 pasos.
1) desactivar el UEFI, desde el setup del bios en la pestaña de boot, en vez de uefi support puse legacy support
2) una vez que booteas desde el livecd para instalar ubuntu, abrís una terminal y pones dmraid -E -r /dev/sdX (en mi caso sdb), y ahí ya aparece el disco al instalar. para que no me borrara windows 8 y no tener problemas, achique la partición previamente desde el administrador de disco en windows.


---

