---
title: "Problemitas con los 64 bits y flash"
date: 2008-01-24
forum: Argentina Team
---

### Post by leonq on 2008-01-24
Muy Buenas....

Millón de gracias por existir....

Soy nuevo en EXTREMO.

Les cuento:

No puedo instalar el plugni para ver flash con el firefox, mejor dicho si puedo, pero no puedo ver sitios con flash..., lei cientos de post pero sigo sin salir del problema, instale restricted areas, desde la pag de addobe, instalando todo por separado, sacando el ubufox....en fin no logro hallar la solucion....espero su amable guia....

con 64 bits vuela, no me gustaria tener que bajarme...

espero un alma caritativa....

Grcias.
LQ

Medita en ESO.

---

### Post by srmantis on 2008-01-25
Para los 64 bits hay un script en el foro x86 64-bit users:
[http://ubuntuforums.org/showthread.php?t=476924](http://ubuntuforums.org/showthread.php?t=476924)
descarga el script que aparece, el enlace es el siguiente:
[http://home.comcast.net/~ubuntume/nspluginwrapper-install-0-1.8.5-3.tar.gz](http://home.comcast.net/~ubuntume/nspluginwrapper-install-0-1.8.5-3.tar.gz)
lo descomprimes y doble click sobre getflash y eliges ejecutar por terminal, sigue las instrucciones y al final te pedira tu nombre de usuario (el mismo con el que entras a ubuntu)

---

### Post by ariel on 2008-02-02
La solucion mas facil en 7.10 es instalar el package "ubuntu-restricted-extras" con synaptics. Funciona en 32 bits y tb. 64bits. ya no hacen faltan wrappers ni parches etc.

despues de instalar, reinicia la maquina.

---

### Post by facundocorradini on 2008-02-02
Pues algo muy raro, que alguno habrán notado, es un error de compatibilidad entre Ubufox y la última versión de Flash que ha causado errores al tratar de instalar flash en equipos nuevos, y problemas varios (por ejemplo, a mí me mataba el procesador) cuando se está viendo un sitio con flash en máquinas que ya lo tenían instalado..

La solución es quitar flash y ubufox, luego reinstalar el flash desde el firefox, y sale andando.

---

### Post by dondionisio on 2008-03-11
**sudo apt-get install flashplugin-nonfree**
y anda el flash player 9 en 64 bit. [ver más detaye]("http://www.psicofxp.com/forums/gnu-linux.50/562126-howto-flash-player-9-kubuntu-ubuntu.html")

---

