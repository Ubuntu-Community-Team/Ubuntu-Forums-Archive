---
title: "Ubuntu 8.04 computadoras en red"
date: 2008-05-19
forum: Argentina Team
---

### Post by cere.nofx on 2008-05-19
que tal gente, tengo dos computadoras con ubuntu 8.04 instalado, una portátil (dell inspiron 1525) y una de escritorio.. la cuestion es que no se como hacer para conectarlas en red para pasar archivos de la computadora de escritorio a la portatil.. tengo un cable de red pero no tengo idea de como conectarlas para compartir los archivos que me quedaron en la pc de escritorio y moverlos a la portatil si alguien puede ayudarme seria genial, muchas graciassssssssssss!! 	:lol:

---

### Post by faktorqm on 2008-05-19
Hola, tenes que conectarlas entre si con un cable que se llama "cruzado". Para saber si es cruzado o derecho, mirá las dos fichitas de la punta, si tienen el mismo orden de colores de izquierda a derecha, es derecho y no te sirve. Si NO tienen el mismo orden de colores, te sirve.
Ponele a una pc la direccion ip 192.168.1.1 con mascara 255.255.255.0 y a la otra 192.168.1.2 con mascara 255.255.255.0 y ahi ya las tenes configuradas para que se "vean".
Para compartir lo podes hacer con NFS, pero la verdad nunca lo hice, por lo tanto desconozco. Aca tenes mi tutorial de samba para hacerlo. Samba es aparte para compartir entre linux, para compartir entre windows y linux tambien te sirve. Es sencillo, leelo y vas a compartir todo. Salu2!!

[http://ubuntuforums.org/showthread.php?t=795418](http://ubuntuforums.org/showthread.php?t=795418)

---

