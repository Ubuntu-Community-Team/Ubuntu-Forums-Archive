---
title: "Grub no carga Windows XP"
date: 2007-04-22
forum: Argentina Team
---

### Post by walden2 on 2007-04-22
Buenas nuevamente. Para los que se acuerdan yo estaba pidiendo ayuda para instalar Ubuntu allá por principios de Marzo. Ahora que salió Feisty, acá estoy, desde Ubuntu pidiendo nuevamente ayuda.
Instalé lo más bien Ubuntu 7.04 amd64 en el mismo disco que tengo Windows XP. Anda bárbaro... pero cuando quise entrar al XP desde Grub... nada. No carga, se queda negra la pantalla, reinicia, aparece Grub, hago nuevamente el intento, aparece la pantalla para elegir el modo seguro de XP, elijo la última configuración que funcionó y reinicia, apareciendo Grub nuevamente.

Resumiendo, sólo puedo entrar a Feisty. Cualquier intento de elegir XP desde Grub resulta en el reinicio de la compu. ¿Qué hago? Por las dudas, en el archivo menu.lst, la sección de XP aparece así:

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1

No creo que este mal, ya que solo tengo un disco rígido con las particiones para XP y Ubuntu.
Espero sus sugerencias.

---

### Post by undiaperfecto on 2007-04-22
y no probaste entrando en modo a prueba de fallos?

---

### Post by walden2 on 2007-04-23
> **undiaperfecto said:**
> y no probaste entrando en modo a prueba de fallos?

Si, probé. Pasa exactamente lo mismo: se reinicia la compu y vuelve al Grub.

---

### Post by walden2 on 2007-04-26
Bueno gente, gracias por nada. Metiendo mano mal me mandé un moco con el booter de XP, tuve que formatear e instalar todo de vuelta. Ahora anda bien y el hecho que pude instalar Beryl sin problemas me calmó bastante. Suerte.

---

