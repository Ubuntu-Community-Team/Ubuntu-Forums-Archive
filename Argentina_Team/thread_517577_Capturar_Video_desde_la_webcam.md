---
title: "Capturar Video desde la webcam"
date: 2007-08-04
forum: Argentina Team
---

### Post by matog on 2007-08-04
Hola gente.
Existe algun programa que me permita grabar el video que capturo con mi webcam? (es usb, y está andando perfecto en Feisty AMD64)

Gracias!

---

### Post by kowal on 2007-08-04
Hay varias formas de capturar video.. 

Te tiro una:

Con freej.

```
sudo aptitude install freej
```

```
freej /dev/video0 -s 320x240 -e captura.ogg
```

Con control+w empieza a grabar/deja de grabar.

Saludos

---

### Post by matog on 2007-08-05
Baje el freej, porque no lo tengo en los repos (no debe estarpara amd64). Tuve que forzar la instalación porque es solo para 586, pero no me funcionó. 

mato@mato-desktop:~$ freej
freej: error while loading shared libraries: libvorbisenc.so.2: wrong ELF class: ELFCLASS64

Con el VLC se puede, [acá]("http://ubuntuforums.org/showthread.php?t=143732") dice como. Pero tiene una contra: no ves lo que estás grabando. Si después, cuando abrís el archivo que te genera, obvio.

Saludos!

---

### Post by kowal on 2007-08-06
En x86 Freej funciona bien (y ves lo que estás grabando). 

Uhm.. también podés probar con mencoder.. pero igual que VLC no ves lo que grabás.

---

### Post by matog on 2007-08-07
Si alguien tiene una versión de FreeJ para AMD64...agradecido ;)

---

### Post by kowal on 2007-08-07
Según estuve investigando un poco hay problemas para compilarlo en amd64..

Otra opción sería probar con un chroot de 32 bits (no uso la versión 64 bits, asi que no puedo ayudarte mucho en esto):

[http://www.guia-ubuntu.org/index.php?title=AMD64](http://www.guia-ubuntu.org/index.php?title=AMD64)

Saludos.

---

### Post by matog on 2007-08-07
Gracias!!! Pruebo y te digo...pero soy un novato...

---

