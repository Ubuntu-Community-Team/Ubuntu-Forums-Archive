---
title: "Ubuntu 7.10 sale victorioso en el PWN to OWN"
date: 2008-03-30
forum: Argentina Team
---

### Post by pante on 2008-03-30
[font=Times New Roman][SIZE="3"][i]**Ubuntu 7.10 sale victorioso en el PWN to OWN***

El MacBook Air fue hackeado en el concurso "PWN to OWN" en solo 2 minutos aprovechando según parece algún bug de seguridad de Safari. El siguiente en caer ha sido Windows Vista.

El último día del concurso permitieron a los participantes aprovechar vulnerabilidades de aplicaciones de terceros. Fue entonces cuando Shane Macaulay consiguió comprometer al equipo que corría el Windows Vista aprovechando un exploit que tiene como responsable al Flash de Adobe.

Finalmente, la portátil Sony Vaio corriendo Ubuntu 7.10 fue la victoriosa del evento, dado que nadie pudo explotar una vulnerabilidad de forma satisfactoria ni siquiera utilizando software de terceros.

Según LinuxWorld en el concurso algún participante conocía la forma de comprometer a la maquina con Ubuntu, pero al parecer ninguno se sentó a desarrollar el exploit.

¿Es posible que el respeto por linux de parte de la comunidad hacker haya influido de alguna forma en el desarrollo del PWN to OWN?
[/i][/SIZE][/font]

Fuente: [**Historias de queso**](http://historiasdequeso.blogspot.com/2008/03/ubuntu-710-sale-victorioso-en-el-pwn-to.html), [**Linux World**](http://www.linuxworld.com/news/2008/032908-with-vista-breached-linux-unbeaten.html) y [**el Foro**](http://ubuntuforums.org/showthread.php?t=739378).

*[SIZE="1"] PWN 2 OWN era un concurso en la conferencia sobre seguridad **CanSecWest Vancouver 2008** donde quien consiguiera vulnerar la seguridad de uno de tres portátiles, se quedaba con el mismo. Eran un VAIO VGN-TZ37CN con Ubuntu 7.10, un Fujitsu U810 corriendo Vista Ultimate SP1 y un MacBook Air con su OSX 10.5.2. Más info [**aquí**](http://cansecwest.com/post/2008-03-20.21:33:00.CanSecWest_PWN2OWN_2008)
[/SIZE]

Saludos* :)

---

### Post by Hei Ku on 2008-03-30
Algunas aclaraciones:
- el objetivo del concurso era utilizar vulnerabilidades no conocidas (0-day exploit)
- Las tres notebooks aguantaron los ataques remotos el primer dia
- El segundo dia, que se permitian solo visitar paginas web (sin clickear en nada) y e-mail (sin abrir attachments) cayo la MacBook Air por una vulnerabilidad en Safari
- El 3er dia, con aplicaciones de 3ras partes, cayo Vista por una vulnerabilidad en Adobe, no me acuerdo si Flash o Acrobat.
- Ubuntu resistio todo el concurso.

---

### Post by PatoDB on 2008-03-31
> **Hei Ku said:**
> 
- El 3er dia, con aplicaciones de 3ras partes, cayo Vista por una vulnerabilidad en Adobe, no me acuerdo si Flash o Acrobat.


Segun he leido en distintos Blogs, la Vulnerabilidad estaba en Adobe Flash... :S


Y la verdad.... me desiluciono mucho Mac... :P

---

### Post by niko_3100 on 2008-03-31
Y encima te cobran una fortuna la macbook con el SO... puuuff!!! como odio la politica de venta de apple con sus precios, admito que los diseños son lindos e innovadores pero su precio y su politica de... queres algo bueno compralo aparte me **** mucho, a mi particularmente me molesta mas Apple que windows.

---

### Post by guisheca on 2008-03-31
Que bueno che, muy buena noticia.

---

### Post by PatoDB on 2008-03-31
> Concluyó el desafío "PWN 2 OWN" de la conferencia CanSecWest, que tenía U$S 20.000 en premios para repartir entre quienes pudieran hackear primero una MacBook Air con Mac OS X 10.5 "Leopard", una laptop Fujitsu U810 con Windows Vista Ultimate SP1 y una Sony VAIO VGN-TZ37CN con Ubuntu 7.10, todas actualizadas con sus últimos parches de seguridad disponibles.

La primera en ser hackeada fué la MacBook Air, gracias a un exploit todavía no corregido en su navegador Safari. Charlie Miller, quién logró hackearla al segundo día del concurso, se llevó U$S 10.000 y la flamante nueva portátil de Apple.

**La segunda en ser hackeada fue la Fujitsu, aparentemente, por un bug multiplataforma en Java, que también podría afectar a los otros 2 sistemas operativos.** Shane Macaulay, el hacker del Windows Vista Ultimate SP1, ganó U$S 5.000 y se llevó la laptop Fujitsu a su casa.

Al terminar el concurso, la Sony VAIO con Ubuntu permanecía imbatible, a pesar de que algunos de los 400 asistentes al evento encontraron errores en su sistema operativo Linux, nadie pudo explotarlos o no quisieron ponerse a trabajar en programar el código necesario para hackearlo.

Fuente: [www.vivalinux.com.ar](www.vivalinux.com.ar)

---

### Post by Hei Ku on 2008-03-31
> **PatoDB said:**
> a pesar de que algunos de los 400 asistentes al evento encontraron errores en su sistema operativo Linux, nadie pudo explotarlos o no quisieron ponerse a trabajar en programar el código necesario para hackearlo.

Ese ultimo comentario, que tambien lo vi en otros articulos, me parece del estilo: yo le hubiera ganado, pero estaba ocupado con otra cosa en ese momento, Pero ya va a ver la proxima. :lolflag:

Hay un dato objetivo, que se aplica al codigo FOSS, y es su calidad. Al menos de los principales proyectos. En promedio, el codigo propietario tiene unos 20 bugs por cada 1000 lineas de codigo. Los principales proyectos open source tienen alrededor de 0,5 o menos. Los bugs mas severos se cierran en cuestion de horas, y el resto se soluciona mucho mas rapidamente. Comparenlo con las vulnerabilidades de MS y Apple, que terminan revelandose porque la gente que los reporto esta harta de esperar AÑOS para que los solucionaran.
Creo que una de las cosas que ayuda es el proceso. Cuando me reportan un bug, es a traves de una lista de correo, o por un sistema de bugs que manda mails a la lista de correos. Miles de personas estan mirando, asi que de pura vergüenza voy a hacer lo posible para solucionarlo. Y si no, alguien mas va a colaborar y solucionarlo, o darme una mano.
Parafraseando lo que se dice de la seguridad, la libertad no es un producto, es un proceso. :)

---

