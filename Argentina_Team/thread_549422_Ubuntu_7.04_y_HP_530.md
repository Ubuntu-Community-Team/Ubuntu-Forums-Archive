---
title: "Ubuntu 7.04 y HP 530"
date: 2007-09-12
forum: Argentina Team
---

### Post by Teno on 2007-09-12
Bien, despues de mi desaparicion del mundo ubuntistico por motivos de tiempo, les cuento que he retomado a full la actividad.

Gracias a Dios, pude adquirir una laptopcita nueva, una HP 530, Core Duo, con 1.5 Gb RAM, y claro, como no podia ser menos, para estrenarle le meti el CD del tio Bill.

Que poco que duro!!!

A las 6 horas (si, 6) ya le estaba pegando una borrada general y metiendole el Ubuntu 7.04, que la verdad anda mas que fantastico.

Debo decir que por suerte no tuve ningun problema en la deteccion del hardware, y si bien hasta ahora lo unico que no he usado fue el modem telefonico, el resto ya fue probado y funciona mas que bien.

Un unico tema fue la resolucion de la pantalla, que no me tomaba los 1280 x 800 nativos, sino que solo llegaba hasta los 1024 x 768. La solucion vino de la mano de una pequeña ayuda, un paquetito llamado 915resolution, el cual, mediante una pequeña edicion y al reiniciar la X, ya estaba andando.

Claro, hay algunas cosas que todavia no capto, por solamente desconocimiento y tiempo, pero la verdad es que anda fantastico.

Gracias a todos por el soporte de siempre y nos vemos en el foro.

Marcelo

---

### Post by niko_3100 on 2007-09-12
Yo tengo una compaq v3415 con sempron 3500+ y 1,5 gb de ram tambien y tomo todo joya hasta la placa de video, claro es nvidia y con ubuntu anda de maravillas.

---

### Post by King Lacho on 2007-09-24
si, eso del 915resolution es genial... jejeje

una preguntilla, alguno de ustedes sabe como puedo configurar mi tarjeta Wireless para que funcione con Ubuntu? Hace ya algún tiempo que he estado tratando de configurarla para mi partición de Ubuntu pero por alguna extraña razón no ha funcionado ni con **bcm43xx-fwcutter** ni con **ndiswrapper**, cualquier ayuda que me puedan dar les agradeceré infinitamente!!!

---

### Post by Teno on 2007-09-25
Que raro, la placa de mi laptop es una Intel 3495 y entro perfecto.

iwconfig no te da bola???

---

### Post by Maximiliano on 2007-10-14
A mi tampoco me funciona la Intel 3945 en el HP 530.
No me aparece en el menú redes ninguna tarjeta (ni inalámbrica, ni cableada), solamente el modem.
Si alguien sabe como solucionarlo, muchas gracias.
Maxi

---

### Post by Teno on 2007-10-15
Fijate en Sistema/Administracion/Gestor de controladores restringidos y fijate si tenes alguno sin tildar.

---

### Post by Maximiliano on 2007-10-28
El gestor de controladores restringidos me pide el paquete linux-restricted-modules-2.6.20-16-generic, y no tengo conexión a internet.

---

### Post by niko_3100 on 2007-10-29
Sin conexion a internet te puedo decir que ubuntu no es muy bueno del todo. Vas a poder instalar lo minimo indispensable y nada mas. Linux nacio en la red, se distribuyo por internet y se actualizaba por la red por eso es que pudo surgir y mejorar, y todavia los linux siguen dependiendo mucho de una conexion a internet lo cual a mi punto de vista es muy bueno siempre y cuando tengas... internet :D

---

### Post by Maximiliano on 2007-10-29
No tengo conexion a internet porque no me funciona la inalambrica.
Sin internet no puedo hacer casi nada. No se porque no aparece en el menu de red la tarjeta, solo aparece el modem convencional.

---

### Post by niko_3100 on 2007-10-29
Y conectate por cable UTP como siempre como es mas convencional igual yo creo que si tu wifi es intel pro wireless te la tubo que haber instaldo de una, yo tengo una anotebook viejita con intel pro wireless 2200 y instale gutsy y me reconocio solo el wifi.

---

### Post by gustmarti on 2007-10-30
Hola Gente, yo también tengo una HP 530 y con ubuntu 7.04 tube el mismo problema, el tema era el driver restringido para la placa Broadcom. Intenté modificarlo desde un tres tutoriales al respecto pero ninguno me dió resultado. La solución vino de la mano de gutsy. Me tomó la placa con el controlador restrigido que vino por defecto y santo remedio.

---

### Post by niko_3100 on 2007-10-31
Mojarela actualizar o instalar a gutsy ajjaja!!!

---

### Post by ma_chro on 2007-11-19
Tengo una hp530, funcionaba bárbaro hasta que queriendo modificar el setting de pantalla para poder ver mejor todo en un cañon, ahora no puedo ver nada.
¿Puede alguien indicarme como volver a reconfigurar desde "recovery mode"? Tengo Gutsy. Muchas Gracias

---

### Post by xpelaox on 2007-11-19
> **King Lacho said:**
> si, eso del 915resolution es genial... jejeje

una preguntilla, alguno de ustedes sabe como puedo configurar mi tarjeta Wireless para que funcione con Ubuntu? Hace ya algún tiempo que he estado tratando de configurarla para mi partición de Ubuntu pero por alguna extraña razón no ha funcionado ni con **bcm43xx-fwcutter** ni con **ndiswrapper**, cualquier ayuda que me puedan dar les agradeceré infinitamente!!!

Tenes instalado Ubuntu 7.10 ? yo con la version anterior tenia que hacer ese baile de ndiswrapper, pero con 7.10 lo isntala solo con los drivers restringidos.

ahh tengo una Notebook HpTx1030la =D

Saludetes

Edit:
ups, no me di cuenta repeti lo mismo xD

> **gustmarti said:**
> Hola Gente, yo también tengo una HP 530 y con ubuntu 7.04 tube el mismo problema, el tema era el driver restringido para la placa Broadcom. Intenté modificarlo desde un tres tutoriales al respecto pero ninguno me dió resultado. La solución vino de la mano de gutsy. Me tomó la placa con el controlador restrigido que vino por defecto y santo remedio.

---

