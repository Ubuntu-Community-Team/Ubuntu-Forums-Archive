---
title: "beryl y ubuntu"
date: 2007-07-09
forum: Argentina Team
---

### Post by Miriknell on 2007-07-09
Buenas, quieria saber si alguein tenia idea de esto..
queria instalar el beryl con unbuntu...
segui un par de pasos que vi en la pagina de beryl...
aparentemente beryl se instalo bien porq en Aplicaciones esta el acceso al panel de control de beryl.... pero no veo los efectos Locos....
Lo que vi es que en la instalacion me dice
...
Warning: You must have xserver-xorg-video-i810installed
If you do not have it already, please install it after setup is completed

Your driver in the Device section should be "i810"
...
Entonces busque para instalar el  xserver-xorg-video-i810installed pero no lo encuentro,el q tengo instalado es  xserver-xorg-video-i810...
alquien tiene alguna idea!
Saludos!!!!

---

### Post by Al_maverick on 2007-07-10
El paquete que tenes esta bien, solo le falta un espacio en el nombre.

Creo que lo que tenes que hacer ahora es iniciar la sesion de Beryl. Ahi varios que lo tienen instalado y te pueden ayudar. En el caso de Compiz lo corres por consola y arranca, Beryl deberia ser similar.

---

### Post by gepatino on 2007-07-10
Tenes que editar el archivo /etc/X11/xorg.conf que es donde esta la configuracion de X, y poner el driver correcto para la placa de red.

Es medio dificil guiarte en esto a ciegas, si podes, copia el contenido de ese archivo aca asi lo vemos y te decimos que cambiar.

---

### Post by Hex_Mandos on 2007-07-10
Che, a mi con activar el driver privativo de mi placa de video + sudo aptitude install beryl me anduvo joya. Es medio a prueba de idiotas.

---

### Post by Miriknell on 2007-07-11
> **gepatino said:**
> Tenes que editar el archivo /etc/X11/xorg.conf que es donde esta la configuracion de X, y poner el driver correcto para la placa de red.

Es medio dificil guiarte en esto a ciegas, si podes, copia el contenido de ese archivo aca asi lo vemos y te decimos que cambiar.

Supongo que quisiste decir"placa de video"

me fije y en ese archivo hay una parte q dice "i810", que se la cambie por "i810installed" y rompio todo pero ya lo arregle.... no se q puede ser....
si puedo pego el archivo...

---

### Post by gepatino on 2007-07-11
perdon, era la placa de video...

Si ya dice i810, entonces esta bien (i810installed no existe, debe ser un error en la cadena de salida del instalador)

Como te dice Hex_Mandos, proba de habilitarlo (si hace falta) desde el gestor de modulos privativos. Si sigue sin funcionar, puede ser que beryl no esté soportado para la combinación de placa de video + driver que viene en ubuntu. (tanto beryl como compiz estan en pleno desarrollo, y no necesariamente funcionan en todas las máquinas)

---

### Post by Hex_Mandos on 2007-07-12
Ahora que lo pienso, i810 es un driver abierto de Intel. Debería andar sin ninguna configuración extra, por lo menos en Feisty.

---

