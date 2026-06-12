---
title: "desinstalar nvidia"
date: 2007-11-20
forum: Argentina Team
---

### Post by lopulus on 2007-11-20
Hola! Otra vez yo!. tengo un problema. Resulta que instale Automix2 y desde alli instale los driver de nvidia y un programa que sirve para montar discos en ntsf y fat32.  Ahora cuando enciendo la maquina hace algunas cosas que antes no hacia y ya no puedo entrar en ubuntu 7.04 como lo hacia normalmente. 
La pantalla (en azul) me dice que no tengo, no se que cosa, y despues de dar aceptar me queda en negro como el viego DOS y con el formato de terminal. Yo supongo que desde alli puedo quitar las instalaciones que hice antes de que se me enquilombe todo y volver a lo que una vez tuve. lo que no se es como desinstalar lo de nvidia. Tengo una geforce mx 4000 de 64M
Espero que me puedan ayudar, como simpre lo han hecho...
muchas gracias ... 

Lopulus-Julian

---

### Post by tzulberti on 2007-11-20
Lo que te esta pasando es que tenes mal configurada la resolucion de tu monitor. Para arreglar eso, una vez que te deja en consola escribi: " sudo dpkg-reconfigure xserver-xorg"

Sino queres usar el driver de nvidia, usa el nv.

---

### Post by Skavenger on 2007-11-21
> **tzulberti said:**
> Sino queres usar el driver de nvidia, usa el nv.
cual es la diferencia entre cada uno?

---

### Post by lopulus on 2007-11-21
Hola: Ya lo pude ver, solo que ahora no puedo usar el mouse, no se mueve. ¿debo utilizar otra vez la misma sentencia?

Gracias de nuevo!

---

### Post by tzulberti on 2007-11-21
Talvez configurastes mal el input del mouse... Fijate que en una de las partes te lo pregunta... 

La diferencia es que el driver nv es libre (en todo sentido), y el de nvidia es cerrado. Ademas, el nv no tiene aceleracion opengl, por lo que no podes usar compiz con ese driver.

---

### Post by Paularg on 2007-11-22
Consejo Sano:

Cada vez que modifiques el uso de drivers de video via automatix o el gestor de drivers restrictivos en la version 7.10, ANTES QUE NADA guardate una version previa del xorg.conf. La misma se encuentra en /etc/X11.

cd /etc/X11

sudo cp xorg.conf  xorg.confaaaammddv  
(donde aaaa es el año, mm el mes y dd el dia y v es la verion 1,2,3 etc en caso que pruebes varias veces con distintas configuraciones)

luego realiza los cambios, y si no anda, simplemente reemplazas la version guardada original  con

sudo cp xorg.confaaaammddv  xorg.conf

luego das <Ctrl> <Alt> <backspace>  y voila !!, retornaste al estado inicial antes de los cambios.

Desde alli investiga en la WEB en los foros o en los HowTos para volver a intentar y corregir el problema.

---

### Post by lopulus on 2007-11-27
Hola gente linda!! 
Quiero comentarles que gracias a su apreciada ayuda pude solucionar los problemas. Se que a veces soy plomo pero a los golpes se aprende. Es por eso que agradezco, ya que tambien pude instalar el CUBO de Beryl.

Una ultima pregunta y no molesto mas (por el momento) ¿Como hago para postear un tuto sencillo de como consegui instalar el CUBO?

Gracias nuevamente!!!!

---

