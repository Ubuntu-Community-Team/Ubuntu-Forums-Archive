---
title: "Instalar Xubuntu con kernel 2.4"
date: 2008-03-05
forum: Argentina Team
---

### Post by jclevien on 2008-03-05
Hola que tal,

Necesito instalar el Xubuntu Gutsy en una maquina virtual QEMU.
Fabrice Bellard (el autor) recomienda que se instalen kernels 2.4 en la maquina guest (supongo que en la host tambien).

El Xubuntu Desktop LiveCD, tiene alguna opcion para instalar esa version del kernel? Se que se puede poner luego de instalar el CD, pero queria saber si viene una opcion por defecto, como en alguna version de Debian.

Gracias.


Juan

---

### Post by jclevien on 2008-03-05
Manana voy a probar el QEMU compilado con soporte KVM, estuve viendo varios comentarios acerca del KVM, del cual dicen que logra velocidades superiores a VMware y VirtualBox.

Tambien vi que en la nueva version de QEMU se incorporo la placa de video VMware SVGA II, con lo que supone una gran mejora.

Muchas gracias.


Juan

---

### Post by jclevien on 2008-03-06
Bueno, estuve probando el QEMU con el driver VMware VGA. Es realmente excelente, pero hay que usar el último snapshot de QEMU para que funcione correctamente (la versión 0.9.1 retorna un core dump).

En cuanto al KVM... una pena, mi micro (Athlon 64 3000) no es compatible con la opción de virtualización de KVM, por lo que no pude chequear la "supervelocidad"... :(

Hasta cualquier momento. Saludos.


Juan

---

