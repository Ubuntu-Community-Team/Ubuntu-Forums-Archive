---
title: "Brasero en ubuntu studio 7.10"
date: 2008-01-22
forum: Argentina Team
---

### Post by h9005 on 2008-01-22
Hola a todos soy nuevo en este foro aunque ya llevo un mes usando ubuntu studio.
Quisiera saber porque mi administrador de paquetes me muestra el brasero 6.10 cuando ya esta disponible para la descarga el 7. Baje desde la pagina en instalador pero no se como hacer para instararlo en la maquina, ya que la version actual no me permite ni grabar ni hacer imagenes. Este es el msj que me tira cuando intento hacer una imagen: Session starting:
	flags			= 8323 
	media type	= 0
	speed		= 0
	track type		= 9
	track format	= 63
	output		= /home/facundo/brasero.iso
job (BraseroDvdcss) set_source
imager (BraseroDvdcss) set_output_type
imager (BraseroDvdcss) set_output
job (BraseroDvdcss) set_task
imager (BraseroDvdcss) get_size
job (BraseroDvdcss) set_task
job (BraseroDvdcss) set_task
imager (BraseroDvdcss) get_track
iter (BraseroDvdcss) stopping
iter (BraseroDvdcss) stopped
job (BraseroDvdcss) set_task
Session error : DVD encriptado: instale libdvdcss versión 1.2.x

---

### Post by margori on 2008-01-22
Hola h9005:

Bienvenido a la comunidad, y veamos si te puedo ayudar con tus consultas.

> **h9005 said:**
> Quisiera saber porque mi administrador de paquetes me muestra el brasero 6.10 cuando ya esta disponible para la descarga el 7.

En los repositorios están disponibles los paquetes de programas que están compilados para la versión de Ubuntu que estás utilizando. Que salga una nueva versión de un programa no significa que inmediatamente va a estar disponible en los repositorios. Hay personas que se dedican a compilar los programas para cada versión de ubuntu y los sube a los repositorios pero no siempre lo hacen con la velocidad que uno quisiera.

> **h9005 said:**
> Este es el msj que me tira cuando intento hacer una imagen: Session starting:
.
.
.
Session error : DVD encriptado: instale libdvdcss versión 1.2.x

Necesitas instalar el paquete libdvdcss 1.2.x. Si no me equivoco esta disponible en los repositorios medibuntu. [Aca]("http://ubuntuforums.org/showthread.php?t=670670") tenes un link con un poco de información. Acordate que San Google puede darte la solución a tus problemas.

Nos vemos. Buena suerte.

---

### Post by facundocorradini on 2008-01-22
> Hay personas que se dedican a compilar los programas para cada versión de ubuntu y los sube a los repositorios pero no siempre lo hacen con la velocidad que uno quisiera.

De hecho, la nueva versióin debe ser auditada y aprobada como "estable" antes de ser subida a los repositorios. 
Yo soy de los que consideran que es mejor tener la versión que está confirmada como estable (la de los repos) que la posiblemente inestable (la última lanzada, descargable desde la web). 
Además, si la bajás de los repos tenés la ventaja de las actualizaciones automáticas, y la instalación limpia.

---

### Post by h9005 on 2008-01-23
Gracias. Está funcionando al menos ahora puedo grabar una imagen. Ya voy a probar las otras funciones. Mil gracias!

---

