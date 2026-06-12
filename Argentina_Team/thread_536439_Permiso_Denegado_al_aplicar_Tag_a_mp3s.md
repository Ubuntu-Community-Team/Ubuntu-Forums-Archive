---
title: "Permiso Denegado al aplicar Tag a mp3s"
date: 2007-08-27
forum: Argentina Team
---

### Post by angeldariodelapuente on 2007-08-27
Hola a todos nose que pasa pero no puedo editarles el ID3 Tag a ningun mp3 y esos que son mios jaja, osea comprobe el permiso en las propiedades de la carpeta y a simple vista esta todo en orden. 

Estoy usando easytag pero tambien intente con el Amarok y todo permiso denegado.

Les dejo un screenshot para que vean el error:

[http://picasaweb.google.com/angeldariodelapuente/Pantallazos/photo#5103261005731234834](http://picasaweb.google.com/angeldariodelapuente/Pantallazos/photo#5103261005731234834)

Saludos!

---

### Post by Mauro22 on 2007-08-27
Hola, 

trata de abrir el easytag desde la consola con el comando sudo

---

### Post by Hei Ku on 2007-08-27
para sacarte la duda que sea un tema de permisos, proba de cambiarle el nombre a alguno de los archivos de esa carpeta.

---

### Post by ubuntu27 on 2007-08-28
Estas usando GNOME, Ubuntu?

Entonces, abre nautilus, anda a la carpeta donde esta tus musicas.

-Selecciona toda las musicas 
-Click derecho/ Propiedades    o Archivo/Propiedades
- En la neuva ventana, anda a "Permisos"
- escoge "Leer&escribir"
- Cerrar


Listo :D

---

### Post by msangil on 2007-08-29
Sólo para eliminar dudas:
Los MP3 están en una partición con formato Linux o los tenés en una partición NTFS / FAT32?
Yo en un momento intené taggear mis MP3 de la partición NFTS y no me dejaba porque no podía escribir en ese formato.

---

### Post by sdm_cacto on 2007-08-29
Ésta es la posta

> sudo apt-get install libtunepimp5-mp3

MP3 Plugin for MusicBrainz tagging library
Libtunepimp simplifies tagging your audio files with the correct data
about artist, album and track title using the MusicBrainz infrastrucure.

---

### Post by Hei Ku on 2007-08-30
Para KDE tenes el juk que tiene varias posibilidades interesantes a la hora de tagear y renombrar archivos.

---

