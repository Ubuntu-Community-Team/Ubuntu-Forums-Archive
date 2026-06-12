---
title: "ktorrent -&gt; utorrent"
date: 2008-04-20
forum: Argentina Team
---

### Post by Fehrant on 2008-04-20
Si me estoy bajando un torrent en ktorrent (ubuntu) y switcheo a Windows y quiero que el utorrent resuma donde el ktorrent dejó, se puede hacer? No traté porque tengo miedo sobreescriba el archivo que ya bajó bastante. Ambos están seteados para poner los archivos en la misma carpeta y todo. 

Y otra pregunta, se puede sacar esa ventana de "select files"? 


Gracias.

---

### Post by pante on 2008-04-20
Si KTorrent y uTorrent tienen la misma carpeta temporal, solo agregas el .torrent a uTorrent y éste detectara los archivos parciales (como si retomaras una descarga interrumpida) y continuará la descarga.

Con eso debería ser suficiente en la mayorí de los casos.

Saludos :)

---

### Post by clasificado on 2008-04-21
no sabia esto :D

Vamos a probar. ¿Alguna consideración en especial o dandole a lo garrotazo alcanza?

clasificado

---

### Post by Fehrant on 2008-04-21
No creo al garrotazo. Me di cuenta de lo siguiente:

La carpeta temporal no es necesariamente donde pone los torrents no terminados. Por default el ktorrent viene con la carpeta /home/[usuario]/.kde/share/apps/ktorrent/ como dump de los archivos temporales, que seguramente no es la carpeta temporal que utiliza el utorrent.

---

### Post by pante on 2008-04-21
Por eso, cuando digo que tienen que tener la misma carpeta temporal implica que esté en una partición a la que se pueda acceder desde ambos sistemas operativos (Linux Ubuntu y Windows). Supongo que KTorrent permite cambiar la ubicación de esa carpeta temporal.

Yo hice esto varias veces con Deluge y uTorrent y no tuve problemas. Con otros P2P (como eMule y aMule) se hace de forma similar.

Saludos :)

---

### Post by clasificado on 2008-04-21
Se puede hacer accesible la particion ext3 desde windows instalándole el driver de ext3 desde 
[http://www.fs-driver.org/](http://www.fs-driver.org/)

en cuanto llegue a casa (y solucione un temita de bittorrent + router) lo pruebo

clasificado

---

### Post by Fehrant on 2008-05-11
Estuve buscando la carpeta de archivos temporales de utorrent (en ktorrent la misma es configurable), pero no pude encontrarla. Alguno sabe?

---

### Post by pante on 2008-05-14
En uTorrent la carpeta temporal se configura desde Opciones -> Preferencias (o Ctrl + P) en la sección Descargas, donde dice "Colocar nuevas descargas".

Saludos :)

---

