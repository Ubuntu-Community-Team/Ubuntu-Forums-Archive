---
title: "Como instalar &quot;cosas&quot; SIN Internet en Ubuntu"
date: 2007-07-09
forum: Argentina Team
---

### Post by djthree on 2007-07-09
Hola, 
Tengo instalado Ubuntu 7.04 pero aún no he podido hacer andar mi modem ADSL USB, por lo cual necesito saber como instalar manualmente aplicaciones, drivers, etc. manualmente en Ubuntu.

Actualmente navego con WIN XP y me bajo las cosas a una carpeta NTFS, que después la leo desde Ubuntu (ya que no puedo bajar las cosas directamente a mi particion EXT3 desde windows)

El problema principal que en este momento me gustaría resolver es como onstalar el NTFS-3G   manualmente para poder escribir en mis particiones ntfs.

Desde ya gracias al que pueda tirarme un par de tips o LINKs para lleer,

Saludos!

---

### Post by marianom on 2007-07-09
Hay otros métodos más prácticos pero te voy tirando este: anda a el buscador de paquetes para Ubuntu ([aca]("http://packages.ubuntu.com/cgi-bin/search_packages.pl?searchon=names&subword=1&version=feisty&release=all&keywords=NTFS-3G") tenes la entrada al paquete que vos necesitás) y ahi vas a tener el paquete listado, si clickeas en él vas a ingresar a las dependencias que también vas a poder descargar.

---

### Post by gepatino on 2007-07-10
Ya vi varias veces la misma consulta, en mi blog puse un post cortito sobre el tema.

[http://gepatino.blogspot.com/2007/07/cmo-instalaractualizar-paquetes-en.html](http://gepatino.blogspot.com/2007/07/cmo-instalaractualizar-paquetes-en.html)

Si les parece lo subo como una nota técnica o mini howto al sitio de uluga.

---

### Post by djthree on 2007-07-10
Garcais por los datos, de momento intente instalar el NTFS-3G, lo baje, pero la intentar instalar me dio error de que faltan las dependencias, asi que hoy voy a probar descargarlas y tratar de instalarlas, supongo debe ser igual que instalar los demas archivos.

Con respecto al link del blog, lo estuve chequean y me ayuda mucho para seguir resolviendo mi tema, lastima de del punto 1. y 2. que si o si necesitas internet para llevarlo a acabo, pero iguakemnte me fue d emucha ayuda! gracias!

ya les contare como me fue,
saludos!

---

### Post by gepatino on 2007-07-10
En cuanto a los puntos que citas... todavía no se como bajar las actulizaciones de listas de paquetes (apt-get update) sin conexión a internet.

Si alguien sabe, que comente y lo agrego al post/howto.

---

### Post by gepatino on 2007-07-11
Bueno, dado que tenía unos minutos libres ;) agregué el contenido del post en un COMO del sitio de ubuntu-ar.

Cuando los editores lo aprueben, se va a poder redirigir este tipo de consultas al sitio.

Saludos,

---

### Post by spg76 on 2007-07-11
> **gepatino said:**
> Bueno, dado que tenía unos minutos libres ;) agregué el contenido del post en un COMO del sitio de ubuntu-ar.

Cuando los editores lo aprueben, se va a poder redirigir este tipo de consultas al sitio.

Saludos,

Recién lo ví, y ya está publicado en [http://ubuntu-ar.org/soporte/comos/instalar-paquetes-sin-banda-ancha](http://ubuntu-ar.org/soporte/comos/instalar-paquetes-sin-banda-ancha)
Saludos.

---

### Post by tony_feisty on 2007-07-28
Podes descargar los paquetes de [http://packages.ubuntu.com/](http://packages.ubuntu.com/) elegis la version que tenés o haces busquedas. etc.

Saludos.

---

### Post by por100pre1 on 2007-07-28
Otra alternativa es grabar en otra pc el [DVD de Ubuntu]("http://nginyang.uvt.nl/") y usarlo como repositorio local...

---

### Post by jpmorelli on 2007-07-28
Por el tema de ntfs-3g nada mas fácil que instalar el paquete:

sudo apt-get install ntfs-config

Te configura la lectura/escritura de particiones ntfs solito con un clik para habilitar la unidad. Yo lo tengo andando y nunca tuve problemas.

---

### Post by guillermolisi on 2007-07-28
Gabriel

Excelente el Blog !!!

Cuando hagas cosas asi, pasa el dato asi uno no se entera de casualidad ... :-)

---

### Post by jpmorelli on 2007-07-28
Encontré una utilidad muuuuy copada que es justamente para actualizar sin internet.
Se llama APTonCD y les paso el link:

[http://www.linux.com/feature/115226](http://www.linux.com/feature/115226)

Parece ser exactamente lo que necesitas.
Suerte !

---

