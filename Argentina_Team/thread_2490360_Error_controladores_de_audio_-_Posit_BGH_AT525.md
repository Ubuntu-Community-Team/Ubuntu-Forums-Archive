---
title: "Error controladores de audio - Posit BGH AT525"
date: 2023-08-31
forum: Argentina Team
---

### Post by aguzknot-26 on 2023-08-31
Hola gente buenas tardes
Me compre una notebook BGH AT525, le instalé ubuntu pero no tengo sonido.
Probe varias cosas buscando en internet, pero no hay una solucion para este modelo.
Por una cuestion familiar voy a utilizarla junto con windows y windows tambien me aparecia tambien el mismo problema con el controlador de audio, incluso de la pagina descargue los controladores y tampoco.
Necesito un alma caritativa que me ayude! Es nueva la maquina!
Gracias!


PD: reinstale alsa y pulseaudio pero nada.
Al subir el volumen me dice "salida ficticia"
Modifique los archivos: etc/modprobe.d/alsa-base.conf y etc/modprobe.d/blacklist.conf agregando unas cosas al final de cada linea.
Ejecute "alsa forced_reload" y nada.
Al ejecutar lspci me aparece el controlador.

---

### Post by lpoli on 2023-09-12
Hola.

Si no te anda en ningún sistema operativo, a priori, estaría roto el integrado de audio o deshabilitado desde la BIOS.
Empezá por fijarte que esté habilitado en la BIOS.

Saludos

---

