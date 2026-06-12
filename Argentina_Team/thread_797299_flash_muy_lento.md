---
title: "flash muy lento"
date: 2008-05-17
forum: Argentina Team
---

### Post by katon on 2008-05-17
queria consultarles si a ustedes tambien les funciona flash en firefox de manera muy lenta como a mi.  ?
lo noto inclusive cuando tengo abierta 1 ventana sola por dar un ejemplo (con un juego de flash ) para ser mas especifico en la pagina facebook.com hay algunos juegos de flash, 
y la diferencia con ese mismo juego en una maquina con windows es increible, en mi pc anda muy lento, y sin tener otros programas abiertos. es como que se ve no "natural" como en camara lenta y encima le bajo la resolucion.
Les dejo aqui las especificaciones de mi pc talvez flash nuevo requiere mucho hardware..
intel pentium 4 1.6 ghz
630 mb ram

---

### Post by katon on 2008-05-18
alguien se le ocurre algo

---

### Post by Hei Ku on 2008-05-19
el problema de flash en linux es archiconocido. una vez por semana hay un thread discutiendo el tema. el soporte de adobe para linux es malo, y las alternativas free todavia no estan maduras. Quizas con la liberacion de la especificacion hace unas semanas eso mejoren.

---

### Post by qntal on 2008-05-19
en osx por ejemplo también es malo pero no tanto como en linux. lamentablemente adobe hace flash para windows nada mas.

---

### Post by katon on 2008-05-19
pero el tema de tener una pc poderosa no ayuda en nada? para que se vea "mas rapido y natural" ?

---

### Post by qntal on 2008-05-19
con esa pc te deberia sobrar, yo con un celeron m 1.73ghz los veo "bien". el tema es que cuando le das pantalla completa muere, ahi si se ve re lento.

lo que podes hacer es darle zoom mediante compiz o instalar el add-on de youtube al totem. desde el totem en pantalla completa los videos se ven bien.

edit:
tenia la cabeza en un thread similar, por eso me fui por lo de youtube. para el tema juegos, es así lamentablemente. podrias crear una maquina virtual con virtualbox y un winxp pelado con 256mb de ram... otra no hay.

---

### Post by katon on 2008-05-19
osea que el tema de los juegos es asi no importa en que maquina sea?

---

### Post by Mauro22 on 2008-05-19
Vas a tener que desinstalar el de adobe e instalar el flash plugin non-free.


Es el unico que safa

:guitar:

---

### Post by Hei Ku on 2008-05-19
Los tres plugins son malos. El de Adobe te come el CPU, los dos free te pinchan la aplicacion o podes ver la mitad de las cosas. Con los sitios flash estas siempre entre la sarten y el fuego. Parte porque la especificacion no era libre, parte porque permite una programacion torpe.

---

### Post by osensei on 2008-05-20
Katon, probá con la versión 9.0.r48 de Adobe Flash Player, a mí me funciona joya. Para conseguirla necesitás bajarte un zip que contiene varias versiones viejas, el zip se encuentra en [http://fpdownload.macromedia.com/get/flashplayer/installers/archive/fp9_archive.zip](http://fpdownload.macromedia.com/get/flashplayer/installers/archive/fp9_archive.zip)

Trae un script de instalación, aunque particularmente yo copié directamente el archivo libflashplayer.so en /usr/lib/opera/plugins, ya que lo uso con Opera y no quería sobreescribir el que instala Ubuntu originalmente, pero supongo que copiándolo en /usr/lib/flashplugin-nonfree debería funcionar con Firefox.

Espero que te sea de ayuda!

Saludos!

---

### Post by qntal on 2008-05-20
uy buenisimo. el 48 era el q mejor andaba.

---

