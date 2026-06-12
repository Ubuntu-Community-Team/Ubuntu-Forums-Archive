---
title: "Consulta de un novato"
date: 2007-07-14
forum: Argentina Team
---

### Post by Tsolo on 2007-07-14
Hola les hace muy poco que instale UBUNTU ya configure el correo y navego por internet sin problemas, pero lo que no se realizar es montar las otras unidades que contienen Windows, tampoco pude instalar programas que baje ya que no se que extension tienen que tener ni como compilarlos.
Estare muy agradecido con cualquier ayuda que me puedad dar.

---

### Post by Hex_Mandos on 2007-07-14
Para bajar programas, usá los repositorios de Ubuntu. Tenés varias maneras de acceder:

1) Menú aplicaciones &#8594; Agregar y quitar programas. Ahí tenes varios cientos de programas para instalar desde una interfaz amigable.

2) Menú Sistema &#8594; Administración &#8594; Gestor de paquetes Synaptic. Desde este menú podés instalar cualquier programa de los repositorios de Ubuntu, pero es menos lndo que el anterior. Podés hacer búsquedas entre alrededor de 20000 paquetes de software distintos.

3) Desde la línea de comandos, tenés aptitude. Tipeás "sudo aptitude install" seguido del nombre del paquete y te lo instala, "sudo aptitude remove" para borrarlo (ej: con "sudo aptitude install inkscape" instalás el programa de diseño de vectores Inkscape). Con "sudo aptitude search" seguido de una palabra clave podés buscar en los repositorios. Si te acostumbrás, es más rápido y es mejor para desinstalar (no te deja paquetes perdidos en tu computadora). 

Si el programa que buscás no está en los repositorios, probá con [GetDeb]("http://www.getdeb.net/"), un sitio que tiene software en los paquetes .deb que usa Ubuntu.

Normalmente, no deberías tener que compilar nada... yo lo hice una sola vez para instalar una versión nueva de FreeCiv. Si querés, después posteo un tutorial corto, pero en serio no lo veo necesario para un uso normal.

---

### Post by ddi4z on 2007-07-14
Gran cantidad de aplicaciones están en los repositorios de Ubuntu

Basta con  ir a Aplicaciones/Agregar y quitar programas para encontrar bastantes, si alguno te convence pues lo marcas y luego de aceptar se empezaran a bajar e instalar automaticamente :)

Por lo de montar otras particiones windows, Ubuntu de manera predeterminada puede leer particiones windows, si lo que quieres es escribir en ellas, solamente necesitas instalar la aplicacion ntfs-3g

desde consola:

$ sudo apt-get install ntfs-3g

te pide la contraseña de root (superusuario) , luego descarga, instala y ya está!

---

### Post by tony_feisty on 2007-07-28
Como te aconsejaron descargate con el synaptic el ntfs-3g, en la ayuda del Ubuntu te explica que tenes que hacer para leer particiones ntfs y fijate para que no tengas problemas de compilacion, que lo que descargues este con extension .deb que son instalables.

Saludos.

---

