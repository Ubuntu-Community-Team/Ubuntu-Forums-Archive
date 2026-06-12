---
title: "Cambio horario 30 diciembre"
date: 2007-12-25
forum: Argentina Team
---

### Post by tychocity on 2007-12-25
Para los administradores y demas, como abordamos el tema del cambio de horario del 30 en Argentina en nuestras redes de computadoras?. Cambiamos la zona horaria???. retocamos el tzdata?.

---

### Post by Skavenger on 2007-12-25
supongo que habra que cambiar a gmt -2

---

### Post by marianom on 2007-12-25
Debería estar llegando al actualizacion de tzdata sola. Habría que ver si los tiempos de empaquetado son satisfactorios.

---

### Post by User21 on 2007-12-26
No es suficiente solo con movernos de zona horaria o reconfigurar el horario manualmente??? o perderemos la configuración del país ? Están íntimamente relacionados los GMT-3 y Argentina ?

---

### Post by facundocorradini on 2007-12-26
La solución ideal sería una actualización de tzdata... pero alguien sabe si eso será así???

---

### Post by rc4nob0 on 2007-12-26
es un bug ?? si pongo el timezone en -2 como deberia ser a partir del domingo me suma
2 a la hora

Your default time zone is set to 'Etc/GMT-2'.
Local time is now:      Wed Dec 26 19:22:58 GMT-2 2007.
Universal Time is now:  Wed Dec 26 17:22:58 UTC 2007.


Ubuntu server 6.10

Saludos!

---

### Post by marianom on 2007-12-26
EDIT: no dije nada, Cuando estoy monotematico no hay con que darle.

---

### Post by marianom on 2007-12-26
> **facundocorradini said:**
> La solución ideal sería una actualización de tzdata... pero alguien sabe si eso será así???

No les queda otra: es la función más importante del tzdata. El problema será ver en cuanto tiempo empaquetan y suben esos cambios. El último que recuerdo fue el cambio de horario en Venezuela y por lo menos a mi me tardó 2 semanas en llegar (claro que era CentOS que tiene que esperar la actualizacion de RedHat pero aca no estoy seguro si no es un upstream de Debian así que una demora lógica habrá).

---

### Post by facundocorradini on 2007-12-26
> **rc4nob0 said:**
> es un bug ?? si pongo el timezone en -2 como deberia ser a partir del domingo me suma
2 a la hora

Your default time zone is set to 'Etc/GMT-2'.


poniendo -2, estás seteando el horario a GTM -2, no quitandole horas....

---

### Post by rc4nob0 on 2007-12-26
y es lo correcto o no?, el horario UTC es el de Greenwich, nosotros tenemos que cambiar la zona horaria, no la hora, pasariamos a estar en GMT-2, pero si seteo la zona como GMT-2 la suma al UTC, no la resta

---

### Post by Hei Ku on 2007-12-26
Esta bien, es lo que va a pasar. El sabado a las 12 de la noche va a pasar a ser el domingo a la 1 de la mañana. O sea, vas a perder una hora de golpe. De facto, vamos a pasar a estar en -2. Al final del verano va a ser a la inversa, y vamos a poder dormir una hora mas.

---

### Post by rc4nob0 on 2007-12-27
> **Hei Ku said:**
> Esta bien, es lo que va a pasar. El sabado a las 12 de la noche va a pasar a ser el domingo a la 1 de la mañana. O sea, vas a perder una hora de golpe. De facto, vamos a pasar a estar en -2. Al final del verano va a ser a la inversa, y vamos a poder dormir una hora mas.

si, eso lo sabemos, pero porque me suma 2 al UMT cuando le seteo GMT-2 ?

---

### Post by newtonfn on 2007-12-27
Ya que estamos en el tema, desde la linea de comando como cambio el GMT ? O no hay una forma de nosotros mismos, temporalmente, actualizar el tzdata ?

---

### Post by jpmorelli on 2007-12-27
En mi laburo ( sistemas de una empresa ) manejamos el tema con gente "especialista en Micro$oft" y nos comentaron que por ahora hay que setear las máquinas en la zona de Brasilia, ya que si bien tiene el mismo GMT -3 que tenemos nosotros, sus gobiernos ya manejan el horario de verano y está previsto.
Por ello al habilitarlo, agrega 1 hora a nuestra hora según el meridiano de greenwich.
Se entendió algo ? :confused:

---

### Post by Hei Ku on 2007-12-27
En el mio los "especialistas" nos mandaron un lindo instructivo explicando como tenemos que cambiar TODOS la configuracion de su PC a GMT -2.
Y yo que pense que la administracion centralizada servía de algo :lolflag:

---

### Post by Luisuntu on 2007-12-28
Hola gente,

Les paso lo que estuve viendo en una distro  Fedora 3. 

Saludos,

Luis

---

### Post by tzulberti on 2007-12-28
Les paso lo que posteo Margarita Manterola (una Debian Developer de arg) en una lista de mails: no lo probe, pero por ahi les funciona:
[http://listas.fi.uba.ar/pipermail/lug/2007-December/026893.html](http://listas.fi.uba.ar/pipermail/lug/2007-December/026893.html)

---

### Post by tychocity on 2007-12-28
esto es lo que hice 

[http://linux.org.ar/pipermail/sgo-gral/2007-December/001719.html](http://linux.org.ar/pipermail/sgo-gral/2007-December/001719.html)

vamos a ver que onda

---

### Post by newtonfn on 2007-12-28
Al final lo que hice fue modificar el zoneinfo de argentina a mano, de una manera muy similar a lo que hizo Tychocity

Seguro me saltará algun mensaje cuando se bajen la actualizaciones de ubuntu con estos cambios, pero por ahora esta excelente para salir del paso.

En el siguiente blog, comenté más o menos los cambios que hice [http://blog.soluciones3f.com.ar/2007/12/28/como-configuro-mi-linux-por-el-cambio-horario-en-la-argentina/](http://blog.soluciones3f.com.ar/2007/12/28/como-configuro-mi-linux-por-el-cambio-horario-en-la-argentina/)

Espero a alguien le sirva, a mi, al menos, me sirvio :)

---

### Post by jpmorelli on 2007-12-29
Este fué el mensaje para los Microbost !!! y pensar que pagan por ello !!!

[http://www.microsoft.com/argentina/dst/]("http://www.microsoft.com/argentina/dst/")

---

### Post by Hei Ku on 2007-12-29
> **newtonfn said:**
> Al final lo que hice fue modificar el zoneinfo de argentina a mano, de una manera muy similar a lo que hizo Tychocity

Seguro me saltará algun mensaje cuando se bajen la actualizaciones de ubuntu con estos cambios, pero por ahora esta excelente para salir del paso.

En el siguiente blog, comenté más o menos los cambios que hice [http://blog.soluciones3f.com.ar/2007/12/28/como-configuro-mi-linux-por-el-cambio-horario-en-la-argentina/](http://blog.soluciones3f.com.ar/2007/12/28/como-configuro-mi-linux-por-el-cambio-horario-en-la-argentina/)

Espero a alguien le sirva, a mi, al menos, me sirvio :)

El archivo tenia un error. En la linea general para argentina, decia 31 en vez de 30. Lo modifique, volvi a aplicarlo y cambio bien la hora.

Gracias!

---

### Post by newtonfn on 2007-12-30
Gracias Hei Ku, me di cuenta de mi error cuando anoche a las 11.30 me dicen que me acuerde de ajustar los relojes de mi casa... y yo con mi mayor cara de incredulidad digo: ¿pero eso no se hace mañana?

En ese momento me que&#341;ia morir, pero bueno, ya era tarde.
Nuevamente, muchas gracias por hacer notar mi error.

(Igualmente espero pronto ver una actualización con los cambios en forma oficial)

---

### Post by Thalskarth on 2007-12-31
> **tzulberti said:**
> Les paso lo que posteo Margarita Manterola (una Debian Developer de arg) en una lista de mails: no lo probe, pero por ahi les funciona:
[http://listas.fi.uba.ar/pipermail/lug/2007-December/026893.html](http://listas.fi.uba.ar/pipermail/lug/2007-December/026893.html)

Yo baje el ".deb" que ponen es ese link y la hora se me andubo de 10 :)

---

### Post by Idus on 2008-01-02
Hoy se actualizó el tzdata, todo normal con la hora.
Rápido, no?

---

### Post by User21 on 2008-01-02
**Confirmado! **TZDATA actualizado! Horario de Argentina conforme al oficial !

Marquen este thread como **SOLVED**!!! :D

---

### Post by jorgito on 2008-01-03
Hola!

Ayer bajo el tzdata, aparentemente sin problemas. No actualizo la hora, pero no me moleste en reinciar asi que no le di importancia. Pero hoy sigue con la hora vieja. Hay que hacer algo mas?

Saludos y gracias!

---

### Post by Hei Ku on 2008-01-03
Tenes configurado que el reloj se ajuste automaticamente con un servidor ntp?

---

### Post by Duyos on 2008-01-03
a mi me llego la actualizacion automatica y no tuve que hacer nada.
MIs repositorios salen del servidor principal y no del de argentina, si no les llego la acutalizacion tal vez eso tenga algo que ver

---

### Post by User21 on 2008-01-04
Una vez hayan obtenido la actualización de tzdata, basta con poner la hora oficial de Argentina, y la misma estará correctamente aplicada, en función de los cambios en el horario oficial de verano. 
Si alguien no obtuvo la actualización de TZDATA, pueden obtenerla actualizando Synaptic o en consola con sudo apt-get update o descargandose el paquete desde launchpad, solo haciendo en:

 [https://launchpad.net/ubuntu/gutsy/i386/tzdata/2007k-0ubuntu0.7.10](https://launchpad.net/ubuntu/gutsy/i386/tzdata/2007k-0ubuntu0.7.10) para Gutsy

[https://launchpad.net/ubuntu/feisty/i386/tzdata/2007k-0ubuntu0.7.04](https://launchpad.net/ubuntu/feisty/i386/tzdata/2007k-0ubuntu0.7.04)  para Feisty

(puede requerir autenticacion en launchpad!)

El paquete se llama tzdata 2007k-0ubuntu0.7.xx . A quienes ya tienen esta update, cerciorarse es el mismo que aparece aqui publicado. GRACIAS!

---

### Post by sajnox on 2008-01-04
> **Hei Ku said:**
> Tenes configurado que el reloj se ajuste automaticamente con un servidor ntp?

Lo mas probable es que todos reciban la actualizacion, pero es igual de importante setear al reloj para que sincronize automaticamente.

Para esto hay que entrar en Sistema y seleccionar la opcion en hora del sistema.

Saludos

---

### Post by jorgito on 2008-01-08
Gracias!

No estaba habilitada (ni siquiera instalada) la actualizacion por ntp.

Ahora anda al pelo.

Gracias de nuevo y saludos!

---

