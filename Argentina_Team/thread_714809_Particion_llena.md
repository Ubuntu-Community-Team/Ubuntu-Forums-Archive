---
title: "Particion llena"
date: 2008-03-04
forum: Argentina Team
---

### Post by h9005 on 2008-03-04
Buenas hice una particion de 10 gb como decía el tutorial para mi ubuntu studio 7.10 y ya está llena! ¿Como hago para sacar lo que no sirve o para ampliarla?

---

### Post by faktorqm on 2008-03-04
te hago una pregunta, el /home a donde lo pusiste? si esta en la misma particion, desde el punto de la vista de la teoria esta mal, tienen que estar separadas. para estirar la particion podes usar gparted, o el viejo pero nunca bien ponderado partition magic. Salu2!

---

### Post by User21 on 2008-03-04
Está llena de programas, o de tus archivos personales, música, películas, etc?
Podes crear otra partición aparte donde dejar tus archivos personales, o podes aumentar el tamaño de la actual con Gparted, desde el cd LIVE de UbuntuStudio o de Ubuntu.

---

### Post by h9005 on 2008-03-04
Jajaja no soy tan nabo che. El sistema de archivos lo hice en una particion de 10gb y el home en otra. Tengo otra con la de intercambio, y dos mas de windows, una ntfs y otra fat 32.

---

### Post by h9005 on 2008-03-04
Ah y no hay un live de ubuntu studio hasta yo se, hay uno en modo texto nomás.

---

### Post by faktorqm on 2008-03-05
y bueno no se, vas a tener que agrandar la particion de alguna u otra manera lo que pasa es que si tenes todo correlativo es un bardo por que si se te cuelga perdes una particion entera..... t lo digo x experiencia.
Ahora, como hiciste para ocupar 10gb? o sea, no se como pudiste haber hecho. Instalaste juegos en /usr/share/games o en /usr/local/games? no puede ser que hayas ocupado 10gb SOLO EN SOFTWARE, no se si me explico.
empeza por borrar los paquetes que bajaste con "apt-get clean". ahi capaz te libera un poco de espacio. Salu2!

---

### Post by h9005 on 2008-03-05
No se, me queda 1,9 gb y para grabar dvd brasero me pide más espacio. En las carpetas que vos decís no hay nada. Ejecuté ese comando con sudo y no pasó nada. Y el klean sweep no funciona.

---

### Post by faktorqm on 2008-03-05
La carpeta que borra (no la carpeta, el contenido) es "/var/cache/apt/archives/" fijate ahi, capaz ya lo borraste, o capaz ya lo limpiaste y no te enteraste.
Si eso esta limpio, la verdad no se....

[[IMG]http://img146.imageshack.us/img146/945/postforohc1.th.jpg[/IMG]](http://img146.imageshack.us/my.php?image=postforohc1.jpg)

Ahi t puse mas o menos como tengo yo los discos, tengo 2 de 160gb. yo tengo casi 500mb en /usr/share/icons y wallpapers y de juegos debo tener 1gb. asi que 1,5gb menos de lo que dice de sistema operativo debo tener.
Para mi que te olvidaste una carpeta muy pesada y no la encontras, o alguna cosa que pusiste mal en algun lado. capaz esta todo bien.... y tenes que morir en un cambio de tamaño de particion. Salu2!!

---

### Post by h9005 on 2008-03-06
Ya revise todo y donde me decis no hay mucho la verdad. Supongo que con las actualizaciones se habrá llenado. :(

---

### Post by Tosh78 on 2008-03-06
Aca encontre algo en UBUNTU-ES que quizas te sirve, chequealo y despues contanos que onda.
[http://www.ubuntu-es.org/index.php?q=node/62047](http://www.ubuntu-es.org/index.php?q=node/62047)

---

### Post by h9005 on 2008-03-13
Bueno voy a chequearlo. Gracias!

---

