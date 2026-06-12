---
title: "Problema al actualizar el Kernel"
date: 2007-07-30
forum: Argentina Team
---

### Post by valucha on 2007-07-30
[COLOR="DarkOrchid"]Ayer reinstalé Ubuntu en mi máquina y quise probar algo nuevo, y antes de cambiar nada en Ubuntu (antes de actualizar y todo) cambié el grub común por uno gráfico como te enseñan en internet.
Todo andaba perfecto hasta que actualicé, y me larga un error al instalar el nuevo kernel...
El error que me tira es algo como que larga un error 2 al tratar de instalarlo.

Tampoco lo vi en el grub al nuevo kernel...

¿Alguien tiene idea?...
[/COLOR]

---

### Post by faktorqm on 2007-07-30
Hola, la verdad que no, pero te recomendaria que postees la salida de dmesg asi los que más saben te pueden ayudar. 
Como es eso del grub grafico? capaz yo vivo en un termo y no me entero de lo mejorcito :(

---

### Post by valucha on 2007-07-30
[COLOR="DarkOrchid"]algo asi 
[http://www.vivalinux.com.ar/distros/grub-grafico-para-ubuntu.html](http://www.vivalinux.com.ar/distros/grub-grafico-para-ubuntu.html)[/COLOR]

---

### Post by faktorqm on 2007-07-31
una pregunta, y si lo solucionas "a mano"? 
Lease, por ejemplo, si tenias la version 2.6.20-16, y actualizaste a 2.6.20-17, basta con cambiar en el /boot/grub/menu.lst esto:

title		Ubuntu, kernel 2.6.20-16-386
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.20-16-386 root=UUID=46ad2827-e3c3-4334-a848-5fa526af7d6e ro quiet splash locale=es_ES vga=792
initrd		/boot/initrd.img-2.6.20-16-386
quiet
savedefault

a esto:

title		Ubuntu, kernel 2.6.20-17-386
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.20-17-386 root=UUID=46ad2827-e3c3-4334-a848-5fa526af7d6e ro quiet splash locale=es_ES vga=792
initrd		/boot/initrd.img-2.6.20-17-386
quiet
savedefault

en realidad te recomendaria que copies, asi generas una entrada mas en el grub, y si no te anda, no hay drama por que no tocaste la vieja. contame como te fue. salu2!

---

### Post by kowal on 2007-07-31
Parece ser un problema del **grub-gfxboot**, probá desinstalar ese paquete y volver al grub normal tal como dicen los ultimos mensajes de este post:

[http://ubuntuforums.org/showthread.php?t=208855&page=43](http://ubuntuforums.org/showthread.php?t=208855&page=43)

Saludos.

---

### Post by valucha on 2007-07-31
[COLOR="DarkOrchid"]Listo ahora ya o solucioné y después tuve que arreglar todo porque también se me había ****** Windows.
Pero no saben de una forma de que la próxima vez que actualice el Kernel no tenga problemas?.[/COLOR]

---

### Post by faktorqm on 2007-08-01
Yo al menos no, lo que te recomiendo es que te informes mas sobre el tema, capaz la macana te la estas mandando vos y no lo sabes por hacer copy-paste de algun tutorial de por ahi. No te lo tomes a mal, te lo digo por ke miles de veces me paso de cosas se rompian ""solas"" y terminaba investigando y aparecian en los foros las guias para que nunca te pasara nada. xD salu2!!!!!!!!!!!

---

### Post by valucha on 2007-08-02
> **faktorqm said:**
> Yo al menos no, lo que te recomiendo es que te informes mas sobre el tema, capaz la macana te la estas mandando vos y no lo sabes por hacer copy-paste de algun tutorial de por ahi. No te lo tomes a mal, te lo digo por ke miles de veces me paso de cosas se rompian ""solas"" y terminaba investigando y aparecian en los foros las guias para que nunca te pasara nada. xD salu2!!!!!!!!!!!

[COLOR="DarkOrchid"]Copi paste hice, pero sabía que era exactamente todo lo que estaba haciendo, es más en un momento en todos los tutoriales te "obligan" a que te fijes en dónde está instalado el grub original, por lo que me tuve que poner a investigar un poco.

pero no sé, voy a seguir viendo que onda, gracias :)[/COLOR]

---

