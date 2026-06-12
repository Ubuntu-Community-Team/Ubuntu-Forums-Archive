---
title: "APT para varias PCs"
date: 2007-01-10
forum: Argentina Team
---

### Post by beuno on 2007-01-10
Para todos los que tienen redes con varias PCs, encontré [un artículo muy bueno]("http://ubuntu-tutorials.com/2007/01/08/save-bandwidth-during-updates-with-apt-cacher-ubuntu-610/") en cómo hacer para que un servidor guarde una copia de todos los paquetes que se bajan, y el resto de las PCs si fijen ahí antes de ir a buscarlo al servidor.
El paquete se llama &#8220;apt-cacher&#8221;, y les dejo las instrucciones rápidas para instalar:

```
sudo aptitude install apt-cacher
```

Editamos: &#8220;/etc/apt-cacher/apt-cacher.conf&#8221;

La linea &#8220;allowed_hosts=192.168.0.0/24&#8243; (permitir a todas las PCs de la subred)

Después editamos: &#8220;/etc/default/apt-cacher&#8221;
Cambiamos &#8220;AUTOSTART=0&#8243; a &#8220;AUTOSTART=1&#8243;

Ahora ejecutamos:
```
sudo /usr/share/apt-cacher/apt-cacher-import.pl /var/cache/apt/archives
```
(esto trae todos los paquetes en esa PC para dejarlos en el cache)

Lo reiniciamos para que tome los cambios:

```
sudo /etc/init.d/apt-cacher restart
```

Podemos comprobarlo en: [http://[LOCAL.IP]:3142/](http://[LOCAL.IP]:3142/)

Listo el servidor.

En los clientes sólo tenemos que cambiar:

```
deb http://archive.ubuntu.com/ubuntu/ gutsy main restricted
```
a
```
deb http://[LOCAL.IP]:3142/archive.ubuntu.com/ubuntu/ gutsy main restricted
```

---

### Post by felipelerena on 2007-01-10
Esta muy bueno, voy a ver si lo implemento en el laburo

---

### Post by facundocorradini on 2008-02-11
Estaba por preguntar y me encontré esto de casualidad.

Esto me va a permitir que las actualizaciones automáticas se bajen solo una vez para todas las compus, no es así?

---

### Post by euzkoarima on 2008-02-12
Buenísimo!!
Por ahora soy el único con linux en el laburo, pero es cuestion de tiempo para convertir al resto. Este tip me facilita un poco más el "trabajo de convertir".

---

