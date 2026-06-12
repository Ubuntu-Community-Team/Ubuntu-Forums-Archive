---
title: "Principiante haciendo destrozos con las particiones"
date: 2007-06-01
forum: Argentina Team
---

### Post by albertof67 on 2007-06-01
Hola gente.. vuelvo a consultarles.. un problema.. instale hace poco el Ubunto 7.04 en mi pc en la cual tengo 2 discos uno de 4 Gb y el otro de 30 GB (en el cual tengo instalado el winxp)

Se me ocurrio para probar el Ubuntu instalarlo en el disco de 4 GB en el cual no me trajo ningun problema.. el problema se me genero en el otro por alguna razon extraña se me perdio la particion..,, buscando en los post encontre el Hiren CD. que sirve para recuperar estos inconvenientes.. con uno de los tantos utilitarios.. (varios en realidad de recuperacion)
me recupera una particion de Fat32 con archivos.. pero ninguno de estos son legibles.. aparecen con caracteres extraños... 

Mi consulta es alguno sabe como solucionar esto o recomendarme algun utilitario??

Desde ya muchas gracias.. 

Alberto (futuru usuario Ubuntu)

---

### Post by Prisma on 2007-06-01
En la particion donde esta el windows XP no puedes acceder a ningun archivo? es como si el disco duro estubiera en blanco?

---

### Post by Prisma on 2007-06-01
No hagas absolutamente nada o vas a ***** el windows, primero contestame la pregunta que te hise en el post anterior

---

### Post by albertof67 on 2007-06-01
Creo que ya es tarde.. estoy pensando en borrar todo.. lamentablemente.. desde Ubuntu monto el disco y se ven cientos de archivos y 3 carpetas pero los nombres son signos.. (@@.,?)(/&& ) de este estilo..

Estuve leyendo un post que habla de como se relacionan el MBR y las particiones.. creo que ahi esta el problema probe con el cd de instalacion de Windows desde la consola de recuperacion un fixmbr y sigue igual.. el cd que comentaba en mi post tiene un monton de utilitarios.. para editar pero no se que poner creo que probando  sin grabar nada podre resolverlo.. algun dia.. jejejeje ..

Gracias por tu rapida respuesta

Alberto (posbile ex usuario Windows..)

---

### Post by Prisma on 2007-06-02
noooooooooo wait, espera no borres nada loko. A mi me paso lo mismo instalando el Ubuntu con wubi y yo repare la particion.

Puedes salvar tu informacion. Has lo siguiente:


reinicia el PC con el cd de windows XP

y presiona R para ir al recovery console

una vez ahi escribe esto:

chkdsk /r

eso va a reparar tu particion. Lo que ha pasado es que el file system se corrompio. Hasme caso, no borres nada todo lo puedes salvar aun.


dejame saber que paso 

suerte

---

### Post by albertof67 on 2007-06-03
Hola prisma.. gracias por tus ayudas.. te cuento hice lo que me digistes y no hay caso.. estuve investigando con los utilitarios.. que te decia del cd y pude detectar que el disco tiene la informacion guardada por suerte !! lo que no tiene es una Fat que apunte a esa informacion aparentemente estoy investigando utilitarios que reparen o reconstruyan la fat , si sabes de algo te agradezco.. 

Un Abrazo..

---

