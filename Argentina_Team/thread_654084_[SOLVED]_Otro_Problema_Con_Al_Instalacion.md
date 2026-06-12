---
title: "[SOLVED] Otro Problema Con Al Instalacion"
date: 2007-12-30
forum: Argentina Team
---

### Post by emiliano_raso on 2007-12-30
Bueno, agradezco el que me hallan ayudado con mi problema anterior, pero ahora otro nuevo me surge (es increible! quiero liberarme de XP!!!)

El tema es el siguiente: Me pide diferentes particiones para la instalacion. Quisiera que me expliquen como es el tema. Estuve leyendo pero mucho no entendi :-S

Lo que me gustaria hacer a mi es esto: Yo tengo un disco de 160GB, particionado ya en dos: "C" de 30GB (que tiene Win XP) y "D" de 130GB que solo tiene archivos y ningun OS.

Me gustaria instalar Ubuntu en la particion "D" sin modificar nada mas, es decir, no tener que formatear nada, simplemente instalarlo en esa particion y listo, como un programa comun. Pero me parece que no se puede.

Espero y agradezco desde ya sus repuestas y soluciones.

Muchas gracias.
Emiliano Raso.

---

### Post by Hei Ku on 2007-12-30
No se puede. Para instalar linux necesita estar en su propia particion. Busca en este foro que hay incontables threads sobre como particionar los discos para instalar.

---

### Post by newtonfn on 2007-12-31
Si bien Ubuntu realmente no se puede instalar como un programa de windows más, por ser un sistema operativo hay dando vueltas por ahí un proyecto llamado Wubi que permite instalar un Ubuntu casi como si fuera un programa más.

Segun dicen, ubuntu se instala en un archivo creado en una partición de Windows, pero luego es igual a una instalación full de ubuntu, con dual boot y todo.

Honestamente nunca lo probé, asi que no podría decirte que tan bien funciona.

Mi consejo es que tomes coraje, hagas espacio en algun apartición e instales Ubuntu como es debido, yo hice eso hace casi un año y no me arrepiento, aún tengo windows como dual boot por si las moscas, pero solo entro para las pocas cosas (juegos) que a veces necesito o quiero hacer y no funcionan en una virtual machine.

Sin embargo, si quieres probar, el proyecto Wubi puede ser una buena alternativa para vos.

Casi me olvido, la web  Wubi, donde además puedes descargarlo, es [http://wubi-installer.org/](http://wubi-installer.org/)

---

### Post by faktorqm on 2007-12-31
me parece que la lo que vos estas planteando es muy simple, agarra cualquier programa que particione, y al final del disco, achicas la de 130. (NO LO HAGAS DESDE QUE TERMINA LA DE XP POR KE SINO VA A INTENTAR MOVER LOS DATOS DE TU "D")
entonces la achicas, con 20 gb te alcanza, te sobra, y tenes para tirar el techo :P
entonces te quedaria por ejemplo:
c- 30gb
d - 110gb
sin particionar - 20gb

cuando arrancas la instalacion le pones al instalador particionamiento manual o que se instale en el espacio libre que tenga el disco (no me acuerdo de memoria las opciones).
Ahi mas o menos te crea una particion para el "/" y otra mas de swap (se recomienda el doble de espacio de tu memoria ram) y listo el pollo. salu2! y feliz año :D

---

### Post by lordpuppet on 2007-12-31
Primero, si quieres instalar ubuntu en la partición "D:" tienes que formatearla de todos modos para darle el sistema de archivo que Ubuntu requiere (ext3), Windows usa NTFS o FAT que es mas viejita.

Instalar ubuntu como lo queres es muy fácil.

Lo que haría yo antes sería, desde Windows, hacer una partición para la SWAP, la memoria virtual para Linux de acuerdo a la cantidad de Ram que tengas.

Luego, desde el cd de instalación, editar la tabla de particiones y donde tienes el disco "D" (donde querés poner Ubuntu) situas el punto de montaje con la barra " / ". y seleccionas el checkbox de formatear (es importantisimo que selecciones que formatee esa particion).
De esta forma le estas diciendo que instale ubuntu en ese disco, la barra "/" es el directorio raíz de linux.

También tendrás que seleccionar en la tabla de particiones, la partición SWAP, eliges punto de montaje "SWAP" y listo.

Le das, siguiente, verificas que no estas accidentalmente formateando la partición de Windows (te darás cuenta por el espacio en GB que tiene cada una).

Asi es como instalo Ubuntu en mis computadoras y funciona. Te recomiendo que antes de instalarlo verifiques que funciona todo desde el Live CD.

PD: encontré un screen que tenia del Editor de particiones del instalador de Ubuntu para mostrarte lo que dije mas arriba:
[http://img119.imageshack.us/my.php?image=screenshot1fm1.png](http://img119.imageshack.us/my.php?image=screenshot1fm1.png)

Un saludo!

---

### Post by emiliano_raso on 2008-01-03
Muchisimas Gracias Gente! Solucionado!

Les Juro  Que Nunca Mas Uso Esa Basura De Windows Despues De Ver Lo Que Es Linux

---

