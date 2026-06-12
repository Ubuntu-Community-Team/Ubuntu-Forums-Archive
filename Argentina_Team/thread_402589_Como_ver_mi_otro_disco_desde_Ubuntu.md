---
title: "Como ver mi otro disco desde Ubuntu"
date: 2007-04-05
forum: Argentina Team
---

### Post by MarcosDV on 2007-04-05
Bueno, como veran soy nuevo en esto de Ubuntu y tengo muchas dudas, es por eso que los molesto con mi 2do post en tan poco tiempo :( pero bueno supongo que despues de todo los foros son para que nos ayudemos entre si...
Resulta que tengo 2 discos, uno de 80gb en el que tengo instalado windows y otro de 40gb en el que tengo instalado mi ubuntu. Tengo toda mi musica en el disco de 80gb pero no puedo acceder desde linux ya que la unidad no me aparece, veo solamente lo que tengo en ubuntu.
Tengo Ubuntu Edgy. Un dato curioso: Antes de hacer el update de dapper a edgy, el disco de 80gb figuraba pero no podia acceder, ahora directamente no figura.

Saludos

---

### Post by kowal on 2007-04-06
Copiá y pega acá lo que te dice el comando** sudo fdisk -l** en la consola (y vemos como te podemos ayudar a editar el archivo **/etc/fstab**)

Es un disco SATA? Tiene particiones en NTFS o Fat32?

---

### Post by MarcosDV on 2007-04-06
Gracias, justo recien lo logre, con un programa que se llama NTFS-3g, lo digo para todos aquellos que tengan el mismo problema, utilizando este programa pude lograr lo que quería, les dejo la guía que use...!

[http://harrolf.blogspot.com/2006/08/linux-ntfs-conseguido-ntfs-3g.html](http://harrolf.blogspot.com/2006/08/linux-ntfs-conseguido-ntfs-3g.html)

Gracias kowal por intentar ayudar ;)

Saludos!

---

### Post by zspikes on 2007-04-06
una pregunta, ese programa sirve para compartir archivos en red con un equipo con win???

pasa q le quiero pasar unos archivos a mi hna y no se como, alguien me da una manito?

gracias!

---

### Post by MarcosDV on 2007-04-06
Mira, yo tengo una maquina en red con windows y desde ubuntu puedo compartir archivos tranquilamente. 
No podes ver los equipos de la red o los ves pero no podes compartir archivos?

---

### Post by zspikes on 2007-04-07
la red me anda porq recibo internet por la misma y anda... el problema es q no veo el resto de los equipos en la red, y ellos no me ven a mi (lo cual no me interesa mucho jeje)

gracias


off: me acabo de dar cuenta q postie en el lugar equivocado jeje... bueno, si no logro resolverlo hago un post nuevo :P

---

### Post by fetova on 2007-04-09
> **zspikes said:**
> la red me anda porq recibo internet por la misma y anda... el problema es q no veo el resto de los equipos en la red, y ellos no me ven a mi (lo cual no me interesa mucho jeje)

gracias


off: me acabo de dar cuenta q postie en el lugar equivocado jeje... bueno, si no logro resolverlo hago un post nuevo :P

Ya checaste que tengan el mismo nombre en red de trabajo?

---

