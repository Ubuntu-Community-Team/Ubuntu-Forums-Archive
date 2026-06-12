---
title: "[SOLVED] Problema con flash"
date: 2008-01-06
forum: Argentina Team
---

### Post by emiliano_raso on 2008-01-06
Bueno, empiezo agradeciendo la ayuda de este foro ya que finalemtne consegui intalarlo correctamente, solo que ahora tengo algunos problemas.

El tema es que instale los plugins de flash, pero hay cosas uqe no las puedo ver directamente y otras (como youtube) que se ve mal.

Aqui les dejo dos screen de lo que me pasa:
- [http://www.subirimagenes.com/imagen-de-Pantallazo-1773783.html](http://www.subirimagenes.com/imagen-de-Pantallazo-1773783.html) (los iconos de las ventanas que se mueven se ven azules)
- [http://www.subirimagenes.com/imagen-de-Pantallazo1-1773799.html](http://www.subirimagenes.com/imagen-de-Pantallazo1-1773799.html) (la ventana del video esta cortada)

Sumado a esto, hay paginas enteras que no puedo ver, ya que  son todo flash.


Otra pregunta es como ahgo para poner Firefox en español? xD me mate leyendo y no encontre la solucion.

Una ultima es: como hago para hacer "accesos directos" de wine para que directamente me ejecute programas con él? No se si me exlico

Desde ya les agradezco muchisimo.

Suerte a todos.

Emiliano

---

### Post by atari130xe on 2008-01-06
Para dejar Firefox en español abrí una consola y tipeá:

 sudo apt-get install mozilla-firefox-locale-es-ar

suerte!

PD cerra el navegador y volve a abrirlo y listo, queda en español :)

---

### Post by emiliano_raso on 2008-01-08
Gente, solucione el problema de Flash. Les dejo como hacerlo para quienes no sepan. Tengan en cuenta que yo recien empiezo a usar Ubuntu y en cuanto a los terminos se muy poo y tal vez me exprese indebidamente.

1) Primero bajen este archivo de internet: [http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_9_linux.tar.gz](http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_9_linux.tar.gz)

2) Luego abran un Terminal

3) Para realizar la instalacion tienen que estar (o ser, no se como se dira) "root", por lo tanto escriban: su root

4) Una vez hayan hecho esto deben ubicarse en el directorio donde descargaron el archivo. El sistema es el mismo que en DOS, es decir, por ejemplo, en mi caso debi poner: cd /media/sda5/Descargas*Firefox
El archivo esta en la carpeta Descargas Firefox, dentro de sda5 (uan de las unidades de disco) dentro de la carpeta media. Recuarden que cuando las carpetas tienen mas de un nombre los espacios se representan con asteriscos "*".

Para conseguir la direccion de una manera facil, simplemente abran la carpeta donde esta el archivo descargado y copien lo que dice en la barra de direcciones (en la parte superior de la carpeta debajo de la barra de archivo bla bla bla...)

5) Ahora copien y peguen esto tal cual está y el archivo se instalara solo. Cuando les pida opciones pongan siempre "y", es decir "yes" para aceptar las diferentes intalaciones.

tar xzvf install_flash_player_9_linux.tar.gz

cd install_flash_player_9_linux

chmod 777 flashplayer-installer

./flashplayer-installer

6) A disfrutar internet!

Espero que les funcione.

Suerte...

"LARGA VIDA AL SOFT LIBRE!!!"

---

