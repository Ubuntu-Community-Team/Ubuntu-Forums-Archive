---
title: "Webcam"
date: 2008-04-09
forum: Argentina Team
---

### Post by carlos cuesta on 2008-04-09
Me han regalado una webcam USB de la marca NOGANET.
Mi Ubuntu 7.10 no la reconoce. He visitado paginas al respecto y no escuentro como hacerla funcionar.
Alguien me puede explicar ? porque soy sumamente nuevo en esto de Ubuntu.
No se compilar ni siquiera el Kernel.
Necesito ayuda ! gracias

---

### Post by Hei Ku on 2008-04-09
yo tampoco lo se compilar, no te preocupes. y el 95% de aca tampoco.

ahora, pone en una terminal lsusb

copia la parte donde aparezcan los datos de la webcam, para ver como avanzamos

---

### Post by carlos cuesta on 2008-04-09
Gracias amigo.
Ahora no puedo enviartelos, pero esta tarde los envio 
mil gracias

---

### Post by mauriciog on 2008-04-09
Carlos:
El soporte para webcams en Linux no es muy completo pero no por esto deberias abandonar la búsqueda de una solución. Existen módulos (drivers) para algunas camaras que funcionan a la perfección en otras.
Podrias intentar utilizando el siguiente link:
[http://www.seismo.ethz.ch/linux/webcam.html](http://www.seismo.ethz.ch/linux/webcam.html)
Exitos en la prueba. Saludos!

---

### Post by carlos cuesta on 2008-04-11
Hola ! Como va ?
Esto es lo que me da, cuando hago Iusb en la terminal.

Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 003: ID 1267:0201 Logic3 / SpectraVideo plc A4Tech SWOP-3 Mouse
Bus 001 Device 001: ID 0000:0000  


Gracias amigo, igual visitare el link que me diste.
Abrazos ! Y si encontras algo extraño en esto que te envio, hacemelo saber.
Saludos

---

### Post by Hei Ku on 2008-04-12
no te la ve a la webcam. por lo que muestra ahi, solo te aparece el mouse.

fijate de cambiarla de puerto usb. anda cambiando, y tira de vuelta lsusb hasta que te aparezca algo distinto.

---

### Post by starbityop on 2008-04-13
el mio dice:

Bus 005 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
Bus 004 Device 007: ID 0c45:6011 Microdia 
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  

Que sigue?? mi webcam no es muy conocida, que me recomiendas hacer? rendirme y comprar una mas conocida :)

saludos!

---

### Post by Hei Ku on 2008-04-13
y... una con un chipset mas amigable estaria buena :D

Aca va el link al driver
[http://www.linux-projects.org/modules/mydownloads/viewcat.php?cid=7](http://www.linux-projects.org/modules/mydownloads/viewcat.php?cid=7)

---

### Post by User21 on 2008-04-14
Yo nunca pude hacer funcionar una Microdia en Ubuntu! Si, tambien soy un usuario tonto! n_n! 

Lo que hice fue cambiarme la webcam con un amigo! xD "Te cambio la webcam, aca tenes el cd de Drivers!.. " :P

---

### Post by mauriciog on 2008-04-14
User21:

Simplemente un genio...

Saludos!

---

### Post by User21 on 2008-04-15
Si cambias la webcam con uno de tus amigos, ponele **[SOLVED]** al hilo! xD
:lolflag::lolflag:

---

