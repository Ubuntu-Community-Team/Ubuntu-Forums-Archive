---
title: "[SOLVED] Se volvio loco el open office"
date: 2008-02-20
forum: Argentina Team
---

### Post by Mataca on 2008-02-20
Hola gente, me paso algo rarisimo acabo de abrir el open office y me encontre con que todo se volvió loco. Parece q se rompio algo de la codificacion de caracteres o no se bien que es.

Abajo les adjunto la imagen, alguna idea??? yo estoy muy perdido.

Gracias!!!

---

### Post by pol666 on 2008-02-20
oh sh***

a mi me paso algo parecido con el Amsn cuando lo usaba, reinstale.

---

### Post by Mataca on 2008-02-21
Ya probe con reinstalar el open office y sigo igual... alguna otra idea?

---

### Post by juanman on 2008-02-22
El problema debe estar en los archivos de configuración de tu usuario... Probá abriendo el OO.org con otro usuario (o con sudo). O renombrando la carpeta /home/usuario/.openoffice.org2 a otro nombre como /home/usuario/.openofficebackup
Es lo q se me ocurre...

Contá como te fue...

---

### Post by Hei Ku on 2008-02-22
Al desinstalar hiciste purge, y despues borraste los archivos de configuracion de tu usuario? Eso puede funcar.

---

### Post by Mataca on 2008-02-26
Gente
Probé varias cosas., lo q me dijo Janus no funciono. Hei Ku me decis como es el comando para hacer purge? yo desinstale desde sinaptic, quiza desde la consola seria mas util.
Gracias!

---

### Post by faktorqm on 2008-02-26
mataca! como t va tanto tiempo!?
tu problema es de configuracion, borra la carpeta /home/tu_usuario/.openoffice.org2 y arranca de vuelta, si te falla, desinstala el openoffice con el apt-get, borra esa carpeta, borra el instalador en /var/cache/apt/archives y reinstala el OO.
creo que la opcion que te nombran del purge es --purge. sino apt-get --help o sino man aptitude. Salu2!

---

### Post by Mataca on 2008-02-27
Bueno lo resolvi, era como me dijeron, solo que no lo entendia :) igualmente ahora instale Xubuntu y estoy copadisimo!!! voy a testearlo a full gracias!!!

---

