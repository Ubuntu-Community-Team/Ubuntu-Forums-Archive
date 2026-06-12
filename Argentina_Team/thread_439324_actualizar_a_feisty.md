---
title: "actualizar a feisty"
date: 2007-05-10
forum: Argentina Team
---

### Post by fetova on 2007-05-10
Hola de nuevo!

Quiero actualizar a feisty con el update-manager y me devuelve este error: :( 

```
Failed to fetch http://security.ubuntu.com/ubuntu/dists/feisty-security/universe/binary-i386/Packages.bz2 El subproceso bzip2 devolvió un código de error (2)
Failed to fetch http://security.ubuntu.com/ubuntu/dists/feisty-security/universe/binary-i386/Packages.bz2 El subproceso bzip2 devolvió un código de error (2)
```

mi /etc/apt/sources.list es:

```

 ## All officially supported packages, including security- and other updates
deb http://archive.ubuntu.com/ubuntu edgy universe
deb http://security.ubuntu.com/ubuntu edgy-security universe

deb http://archive.ubuntu.com/ubuntu edgy universe

 
 ## The source packages (only needed to recompile existing packages)
 
 ## All community supported packages, including security- and other updates
deb http://security.ubuntu.com/ubuntu edgy-security universe
 
 ## The source packages (only needed to recompile existing packages)

```

ya quiero probar feisty!!! quiero ver si es tan maravilloso como cuentan por mi mismo en mi compu!!! :popcorn:

---

### Post by beuno on 2007-05-10
Estas teniendo algun problema con tu ISP.  :(

---

### Post by fetova on 2007-05-10
> **beuno said:**
> Estas teniendo algun problema con tu ISP.  :(

pues he tenido algunos problemas... alguien en prodigy (el ISP) bloqueo la ip del servidor que tiene al portal en que trabajo  ](*,) igual y si :(... entonces tendre que actualizar manualmente?

:( :( Ya me voy a acostumbrar!!! :P

---

### Post by clasificado on 2007-05-11
De ultima bajate el cd de ubuntu y actualizalo desde ahi que tiene una opcion de actualizacion de sistema existente

---

### Post by fetova on 2007-05-11
Pues baje el iso alternativo y ahorita estoy actualizando mi maquina con el :D ... yo creo que si todo sale bien, ya voy a poder ver este foro desde feisty en mi maquina.

Espero que no se truene el X como en cada vez que he actualizado manualmente :p 

saludos desde el live cd de feisty (me acaba de llegar el disco :D, muy bonito :p)

---

### Post by fetova on 2007-05-14
Ya estoy en feisty!!!! \\:D/  \\:D/ 

Ta bonito :)

Pero no me quiere habilitar los efectos de escritorio :( Estos son los informes del desktop-effects ejecutado en terminal:

```
federico@fetova:~$ desktop-effects
nvidia hardware not available
/usr/bin/compiz.real: GLX_EXT_texture_from_pixmap is missing
/usr/bin/compiz.real: Failed to manage screen: 0
/usr/bin/compiz.real: No manageable screens found on display :0.0
Advertencia del gestor de ventanas: La ventana 0 en la pantalla «:0.0» ya tiene un gestor de ventanas, intente usar la opción «--replace» para reemplazar el gestor de ventanas activo.
federico@fetova:~$ desktop-effects --replace
nvidia hardware not available
gtk-window-decorator: Could not acquire decoration manager selection on screen 0 display ":0.0"
/usr/bin/compiz.real: GLX_EXT_texture_from_pixmap is missing
/usr/bin/compiz.real: Failed to manage screen: 0
/usr/bin/compiz.real: No manageable screens found on display :0.0
Advertencia del gestor de ventanas: WM_TRANSIENT_FOR inválido para la ventana 0x3800003 especificada para 0x38003a1 ().

```

:(

Que podria hacer? Gracias de antemano :D

---

### Post by lavaramano on 2007-05-14
@fetova, tenes instalados los drivers de la placa de video? 
si tenes nvidia, es muy probable que puedas instalarlo/habilitarlo desde ahi, y sino hay mucha info sobre nvidia y ati(aunque apeste)

---

### Post by fetova on 2007-05-14
> **lavaramano said:**
> @fetova, tenes instalados los drivers de la placa de video? 
si tenes nvidia, es muy probable que puedas instalarlo/habilitarlo desde ahi, y sino hay mucha info sobre nvidia y ati(aunque apeste)

Pueees... mi tarjeta es una trident CyberALLADIN-T...
Necesito los drivers de nvidia? :confused: 
cuando configure el x-org puse de driver "trident"
Lo cambio?

Gracias por la respuesta tan rapida :)

---

### Post by Al_maverick on 2007-05-14
me parece que esa placa no tiene acelerador 3d, viene integrada en el mother? En ese caso, lo siento pero no hay mucho que se pueda hacer.

---

### Post by lugonesjoaquin on 2007-05-14
> **fetova said:**
> Pueees... mi tarjeta es una trident CyberALLADIN-T...
Necesito los drivers de nvidia? :confused: 
cuando configure el x-org puse de driver "trident"
Lo cambio?

Gracias por la respuesta tan rapida :)
Lamentablemente solo ATI, nVidia y Intel creo que son las placas capaces de correr Beryl.

---

### Post by fetova on 2007-05-15
> **lugonesjoaquin said:**
> Lamentablemente solo ATI, nVidia y Intel creo que son las placas capaces de correr Beryl.

Mmm... ya que :( . de cualquier manera me asaltaron ayer y me rompieron la pantalla de mi lap :cry: :-({|= igual y le cambio de tarjeta o me compro otra :(

Gracias :(

---

### Post by marianom on 2007-05-15
¡Qué mal, fetova! Lo lamento mucho y espero que, fuera de la pérdida material, estés bien. Yo tengo un master degree en asaltos y siempre las primeras veces es horriible.

---

### Post by fetova on 2007-05-15
> **marianom said:**
> ¡Qué mal, fetova! Lo lamento mucho y espero que, fuera de la pérdida material, estés bien. Yo tengo un master degree en asaltos y siempre las primeras veces es horriible.

Jajajaja, pues es feo  y solo es la primera vez que me quitan algo,por que ya van varias, pero nunca me pudieron qutar algo. Me dolia la cabeza a estallar, y me quitaron el dolor con los golpes en la cabeza que me dieron por resistirme :p.

Pero no hay problema, lo unico que no va y viene es el tiempo de vida :D 

Gracias por las palabras!!

---

