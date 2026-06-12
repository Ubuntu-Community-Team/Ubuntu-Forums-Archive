---
title: "[Como] Instalar núcleo kernel 2.6.22 en Ubuntu Kubuntu Xubuntu 7.04 Feisty Fawn"
date: 2007-09-04
forum: Argentina Team
---

### Post by LikeVinyl on 2007-09-04
Hola amigos!

En la actualidad los usuarios de Ubuntu Feisty Fawn 7.04, utilizamos el núcleo 2.6.20-16 generic. Este tuturial explicará cómo actualizar el núcleo a la versión 2.6.22-10-generic.

Importante, el núcleo 2.6.22 estará disponible en la próxima versión de Ubuntu 7.10 -Gutsy Gibbon-, este tutorial está destinado a todos los usuarios que quieran experimentar y probar el núcleo 2.6.22-10-generic antes del lanzamiento oficial de Ubuntu 7.10 Gutsy Gibbon programado para el próximo 18 de Octubre.

Si deseas conocer más sobre los cambios en la versión 2.6.22-10 generic pula [aquí]("http://kernelnewbies.org/Linux_2_6_22")

**Antes de empezar**

Asumiremos que disponemos de Ubuntu, Kubuntu, Edubuntu, Xubuntu 7.04 Feisty Fawn o cualquier distribución basada en Ubuntu 7.04 Feisty Fawn.

Esta guía utiliza gnome y gedit como editor básico de texto, los usuarios de Kubuntu necesitarán utilizar kate o el editor de su preferencia.

Manos a la obra!

**Preparando el sistema**

Primero necesitaremos agregar el repositorio de Gutsy Gibbon (Esto es temporal y únicamente lo utilizaremos para descargar el núcleo).

Desde una consola o terminal dentro de X, invocar el siguiente comando:

> $ echo deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy main restricted | sudo tee -a /etc/apt/sources.list


Luego, será necesario actualizar el sources.list, desde una consola o terminal dentro de X, invocar el siguiente comando:

> $ sudo aptitude update

**Instalación**

Para instalar el núcleo 2.6.22-10 invocar el siguiente comando:

> $ sudo apt-get install linux-headers-2.6.22-10 linux-headers-2.6.22-10-generic linux-image-2.6.22-10-generic linux-restricted-modules-2.6.22-10-generic linux-ubuntu-modules-2.6.22-10-generic


Una vez finalizada la descarga e instalación, quitar el repositorio de Gutsy Gibbon de nuestro sources.list, desde una consola o terminal dentro de X, invocar el siguiente comando:

> $ sudo gedit /etc/apt/sources.list

Aquí podemos remover esta línea o simplemente comentarla (&#8220;comentar&#8221; significa agregar el signo # delante de la línea que corresponde para que no sea tenida en cuenta por el código en cuestión) Línea que debemos remover o comentar:

> #deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy main restricted

Guardar los cambios y cerrar gedit

Luego, actualizar el sources.list, dentro de una consola o terminal dentro de X, invocar el siguiente comando:

> $ sudo aptitude update


Si finalizamos estos pasos sin errores, ya tenemos instalada la nueva versión del núcleo y podemos reiniciar nuestro ordenador.

**Solucionando problemas**

Si experimentamos dificultades, aplicar el siguiente procedimiento para revertir los cambios:

Reiniciar el ordenador y esperar que cargue Grub, pulsar la tecla &#8220;ESC&#8221; y seleccionar el núcleo anterior (posiblemente el 2.6.20-16-*)

**Desinstalando el núcleo**

Desde una consola o terminal dentro de X, invocar el siguiente comando:

> $ sudo apt-get remove linux-headers-2.6.22-10 linux-headers-2.6.22-10-generic linux-image-2.6.22-10-generic linux-restricted-modules-2.6.22-10-generic linux-ubuntu-modules-2.6.22-10-generic


Remover los paquetes del núcleo también removerá la entrada correspondiente en el gestor de arranque Grub, si por algúna razón esto no ocurre aplicar el siguiente procedimiento:

Desde una consola o terminal dentro de X, invocar el siguiente comando:

> $ sudo gedit /boot/grub/menu.lst

Eliminar las siguientes líneas:

> title Ubuntu, kernel 2.6.22-10-generic
root (hd0,0)
kernel /boot/vmlinuz-2.6.22-10-generic root=UUID=34f3806f-36b8-494d-be17-78325684a0a5 ro quiet splash
initrd /boot/initrd.img-2.6.22-10-generic
quiet
savedefault
title Ubuntu, kernel 2.6.22-10-generic (recovery mode)
root (hd0,0)
kernel /boot/vmlinuz-2.6.22-10-generic root=UUID=34f3806f-36b8-494d-be17-78325684a0a5 ro single
initrd /boot/initrd.img-2.6.22-10-generic

Guardar los cambios, cerrrar gedit y reiniciar el ordenador.

**Usuarios con tarjetas nvidia**

Si tienes la última version del controlador nvidia 100.14.11 (descargado e instalado en forma manual) y no puedes iniciar X debido a que este procedimiento instaló los módulos restringidos, aplicar el siguiente procedimiento:

Desde la consola, en modo texto, iniciar sesión con tu nombre de usuario e invocar el siguiente comando:

> $ sudo nano /etc/X11/xorg.conf


Buscar la sección device, debe mostrar algo similar a esto:
> 
Section "Device"
Identifier "nVidia Corporation NV34 [GeForce FX 5200]"
Driver "nvidia"
EndSection

Reemplazar la palabra nvidia de la línea Driver por nv, de manera que quede así:

> Section "Device"
Identifier "nVidia Corporation NV34 [GeForce FX 5200]"
Driver "nv"
EndSection

Guardar los cambios CTRL+O y salir CTRL+X

**Arrancar X**

Para usuarios gnome

> $ sudo /etc/init.d/gdm restart

Para usuarios kde

> $ sudo /etc/init.d/kdm restart

Funcionando!

**Notas finales**

    * Este procedimiento fué probado con éxito en un ordenador Intel Pentium 4 Dual Core 3.0 con 1gb de Ram y video Nvidia Geforce xfx5200 128mb.
    * Esta gúia fué modificada, mejorada y adaptada para nuestra comunidad desde un Cómo [how-to] en Inglés -bastante incompleto por cierto-.

Fuentes:
[http://www.ubuntugeek.com/]("http://www.ubuntugeek.com/")

::: LikeVinyl 2007 :::

Este documento es Copyleft, Miguel Angel Ríos, 2007
Tienes la Libertad de copiar, modificar y distribuir estos contenidos.

---

### Post by leo_rockway on 2007-09-04
Hola, muy bueno este Como. La verdad que diez puntos.
No puedo seguirlo porque hace algun tiempo ya uso Gutsy, pero le va a venir bien a los que quieran probar el nuevo nucleo.

Un solo comentario. Te quedo el link de los cambios del nucleo colgado.

 > **LikeVinyl said:**
> Si deseas conocer más sobre los cambios de la versión 2.6.22-10 generic pula aquí


El link (en ingles) es este.
[http://kernelnewbies.org/Linux_2_6_22]("http://kernelnewbies.org/Linux_2_6_22")

De nuevo, gracias por traer este Como al foro!:guitar:

---

### Post by niko_3100 on 2007-09-04
Que mejoras trae ese nucleo? la verdad que el feisty me parece comodisimo. Otra cosa yo tengo una placa de video geforce 6150 en mi notebook v3415 podre actualizar los drivers mas recientes? porque tengo u problemita con el briillo que cuando lo modifico se me va o todo brillo mal o todo oscuro tengo que modificarlo en el grub para usar los terminos medios. Gracias.

---

