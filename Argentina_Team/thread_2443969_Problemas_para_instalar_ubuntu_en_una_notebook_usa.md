---
title: "Problemas para instalar ubuntu en una notebook usando pen drive (BIOS horrible)"
date: 2020-05-22
forum: Argentina Team
---

### Post by mustufar1 on 2020-05-22
[COLOR=#1C1E21][FONT=Helvetica]Hola!
 Tengo un problema con una notebook del año 2016. Po[/FONT][/COLOR][COLOR=#1C1E21][FONT=Helvetica]r error tiene instalado un SO Debian Buster de 64-bit y la máquina es de 32-bit... con lo cual se cuelga, no tiene sonido y no es confiable para trabajar. Como no tiene lectora de CD tengo que instalarle un nuevo SO (pensaba en algún ubuntu 14 o un lubuntu) usando un pen drive al que le grabé la imagen iso usando rufus. El problema es que la bios de esta máquina es tan precaria que no ofrece muchas opciones para cambiar la configuración de arranque y por motivos que desconozco, nunca logro que arranque desde el pen drive. Aquí les comparto algunas fotos de las características de la Bios y de los mensajes que me aparecieron en mis intentos infructuosos por instalar el nuevo SO Desde ya, muchas gracias por la ayuda que puedan brindarme.[/FONT][/COLOR]

---

### Post by CelticWarrior on 2020-05-25
Bienvenido.

Por favor indicanos las especificaciones de hardware completas.

> [COLOR=#1C1E21][FONT=Helvetica]tiene instalado un SO Debian Buster de 64-bit y la máquina es de 32-bit[/FONT][/COLOR]
Esto es incorrecto, imposible. SOs de 32-bit se pueden instalar en hardware de 64-bit pero al revés no es posible. Eso si, puede tratarse de un CPU "Bay Trail" o "Cherry Trail" que aunque siendo procesadores de 64-bit suelen venir acompañados de una UEFI de 32-bit, la cual necesita/necesitaba pasos adicionales para instalación. Creo que ahora es posible arrancar y instalar correctamente con la imagen padrón de Ubuntu y derivados pero después de instalado si necesita configuraciones adicionales para que funcione. Pero hay que instalar siempre Ubuntu 64-bit, que quede claro.

Hay un "respin" de Ubuntu que incluye mejor suporte para las partes que no funcionan correctamente: [http://www.linuxium.com.au/isos](http://www.linuxium.com.au/isos)
Pero asegurate de que el tuyo es uno de esos antes de usar.

---

### Post by emanueledb on 2020-07-04
intenta arreglar la lectora

---

