---
title: "Puedo instalar Ubuntu y Edubuntu en un solo equipo?"
date: 2007-09-12
forum: Argentina Team
---

### Post by rafagomez24 on 2007-09-12
Saludos,

Espero alguien me pueda ayudar.

Tengo una notebook Dell Latitude D610 a la que le instalé Ubuntu 7.04, pero quiero intentar instalarle Edubuntu en otra partición del disco para tener Ubuntu y Edubuntu en un sólo equipo.

Alguien sabe como lo puedo hacer?

Gracias

---

### Post by sajnox on 2007-09-12
simplemente bootea desde el cd e instalalo, obvio que tenes que tener muy claro el tema de particiones del disco para saber como instarlo, cuando genere el grub el se encarga de las modificaciones.

Otra opcion mas que valida es correr el edubuntu desde una maquina virtual (virtualbox), pero para eso necesitas minimo 512mb de ram

Saludos,

---

### Post by ubuntu27 on 2007-09-13
Edubuntu es Ubuntu con programas educativos mas un servicio especial para Edubuntu que te permite ejecutar aplicaciones desde un servidor (bueno para computadoras con poco espacio en el disco duro, o que no tiene disco duro). 

Realmente no veo una razon para instalar Edubuntu, al menos que estes en una escuela :D

Edubuntu usa el mismo repositorio que UBuntu, asi que podras instalar paquetes de edubuntu en Ubuntu tambien.. :)

---

### Post by faktorqm on 2007-09-13
hola, yo una vez tenia un guindous y 3 linux en la misma pc. si, tengo discos grandes, si esa es tu duda.
el grub se autoactualiza, no te preocupes. el truco consiste en no hacer 74 particiones, sino hacer las necesarias para instalar los linux y LA MISMA PARTICION DE SWAP PARA TODOS. salu2!!

---

### Post by rafagomez24 on 2007-09-20
Muchas gracias por tu respuesta.

Pero me surgió otra duda, espero me puedas ayudar.

Tengo un programa de windows (.exe) que me gustaria instalarlo en Ubuntu. Existe alguna herramienta que me permita instalar este programa?.

Saludos

---

### Post by sajnox on 2007-09-20
podes hacerlo con wine, lo tenes instalado??

sino lo tenes, lo podes cargar desde el synaptic y una vez que lo tenes al .exe click derecho y seleccionas abrir con wine

Saludos

---

### Post by por100pre1 on 2007-09-20
Sería bueno saber cual es el programa de desea instalar. No todos los programas de Windows se pueden correr en Ubuntu con WINE.

---

### Post by martincho90 on 2007-09-21
> **rafagomez24 said:**
> Saludos,

Espero alguien me pueda ayudar.

Tengo una notebook Dell Latitude D610 a la que le instalé Ubuntu 7.04, pero quiero intentar instalarle Edubuntu en otra partición del disco para tener Ubuntu y Edubuntu en un sólo equipo.

Alguien sabe como lo puedo hacer?

GraciasClaro, eso se llama "multiboot".
Deberias hacer espacio para alojar la nueva, por ejemplo usando "qtparted": "sudo apt-get install qtparted"
Despues le pones lo que quieras, edubuntu o la distro que se te ocurra.
Qualquier instalador te va a pedir que le definas la particion swap, que seguramente la reconocera automaticamente, ahi deberias usar la misma que tenes ahora (como te indicaron antes), y despues que le definas donde queres el /, ahi deberia ser el espacio que creaste.
Seguramente edubuntu te va a decir que al instalar el grub reconoce otra sistema operativo (tu ubuntu actual) y ya, asi de simple.

---

