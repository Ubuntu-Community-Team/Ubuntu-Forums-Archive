---
title: "vnc"
date: 2008-03-10
forum: Argentina Team
---

### Post by kha0s101 on 2008-03-10
Hol

---

### Post by User21 on 2008-03-10
HOLA, que tal! ¬_¬

---

### Post by felipelerena on 2008-03-10
cuak

---

### Post by jpmorelli on 2008-03-10
??? ):p

---

### Post by kha0s101 on 2008-03-10
[COLOR="DarkGreen"]Juas!! Estaba creando un post sobre vnc cuando dí con la utilidad que necesitaba y decidí cerrar el post, por error lo envié pero creí que no había salido!!! :mad: 

sorry :lolflag:

Aprovecho sin embargo, para no "malgastar" el thread y pregunto:

Tengo 2 pcs con Ubuntu 7.10 conectadas por un cable cruzado. Cuando inicio la que se conecta al modem si lo hago con XP, la 2ª máquina se conecta perfectamente y puedo navegar en ambas máquinas. Cuando ambas inician en Ubuntu, no hay forma de conseguirlo.

* Que pasos debo seguir para solucionar esto?

* Como logro que ambas máquinas se "vean"?

Por cierto, ambas máquinas parecen conectar sin problemas a la red porque el ícono dice "conexión de red cableada"

Saludos y gracias por todas las respuestas, he logrado dejar el güin2 gracias a Ubuntu y a este gran foro. Me siento como cuando dejé de fumar ;)[/COLOR]

---

### Post by gmunioz on 2008-03-14
Hola kha...:

Cambia las ips por las que correspondan a tu red.
1) Configura asi los archivos:

a)

/etc/network/interfaces de la PC con internet:

# The loopback network interface

auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
address 192.168.1.181
gateway 192.168.1.180
netmask 255.255.255.0
network 192.168.1.0
broadcast 192.168.1.255

b)

 /etc/network/interfaces de la pc sin internet:

 
# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
address 192.168.1.180
gateway 192.168.1.181
netmask 255.255.255.0
network 192.168.1.0
broadcast 192.168.1.255

2) Para compartir archivos, requieres de nfs

En la pc servidor

Sistema > Administración > Carpetas compartidas pregunta que sistema, elegir NFS e instala los paquetes necesarios.
En la pantalla emergente
Añadir la carpeta a compartir
Poner la ip de la maquina cliente.
Ejecutar en consola:

sudo gedit /etc/exports

# /etc/exports: the access control list for filesystems which may be exported
#        to NFS clients.  See exports(5).
#
# Example for NFSv2 and NFSv3:
# /srv/homes       hostname1(rw,sync) hostname2(ro,sync)
#
# Example for NFSv4:
# /srv/nfs4        gss/krb5i(rw,sync,fsid=0,crossmnt)
# /srv/nfs4/homes  gss/krb5i(rw,sync)
#
Agregar en nombre de la carpeta a compartir (por ejemplo /media/share y la ip del cliente)

/media/share       192.168.1.180(rw,async)

sudo gedit /etc/hosts.deny

Agregar:

portmap:ALL
lockd:ALL
mountd:ALL
rquotad:ALL
statd:ALL

sudo gedit /etc/hosts.allow

Agregar:

portmap:192.168.1.180/255.255.255.0
lockd:192.168.1.180/255.255.255.0
mountd:192.168.1.180/255.255.255.0
rquotad:192.168.1.180/255.255.255.0
statd:192.168.1.180/255.255.255.0

En la pc cliente instalar los paquetes nfs, copialos de /var/cache/apt/archives/  del servidor e instalalos con

sudo dpkg -i *.deb 

Crear la carpeta donde se montará la carpeta a compartir, por ejemplo /home/usuarios/share:

Ejecutar:

mkdir /home/usuario/share

Ejecutar para montar

sudo mount -t nfs 192.168.1.181:/media/share /home/usuario/share

Para montaje automático, ejecutar:

sudo gedit /etc/fstab

En el fstab del cliente.

192.168.1.181:/media/share /home/usuario/share nfs rsize=8192,wsize=8192,timeo=14,intr,user,auto

3) Compartir internet

Para compartir la conexión a internet  con un proxy Squid

sudo apt-get install squid 

Una vez que lo tienes instalado, lo pones en marcha asi:

sudo squid start

o con
 
sudo squid

Si quieres que te arranque en el inicio del sistema, puedes hacer un script en "/etc/init.d" llamado "squid"
que contenga esto:

/usr/local/squid/sbin/squid &

le das permisos de ejecución

sudo chmod +x squid

y lo pones en el arranque de tu sistema de esta manera:

sudo ln -s /etc/init.d/squid /etc/rc2.d/S99squid
sudo ln -s /etc/init.d/squid /etc/rc3.d/S99squid
sudo ln -s /etc/init.d/squid /etc/rc4.d/S99squid
sudo ln -s /etc/init.d/squid /etc/rc5.d/S99squid

Para configurar squid, basta configurar el fichero "squid.conf"

sudo gedit /etc/squid.conf

Suponiendo tu red local es del tipo 192.168.1.0/255.255.255.0

Debes prestar atención a los siguientes items:

http_port 3128
(este es el puerto por el que escuchara squid)

cache_mem 8
(tamaño máximo que pueden alcanzar los objetos cacheados, sería
recomendable ponerlo a 16 MB ya que posees varios clientes).

cache_dir ufs /var/spool/squid 100 16 256
(es el directorio donde se almacenará la caché
y como se estructurará éste. No lo toques)

acl all src 0.0.0.0/0.0.0.0
(creas una lista de acceso con todas las redes)

acl localhost src 127.0.0.1/255.255.255.255
(creas una lista de acceso con
la propia maquina)

acl mired src 192.168.1.0/255.255.255.0
(creas una lista de acceso con tu red)

http_access allow localhost
(permites el acceso a la propia maquina)

http_access allow mired
(permites el acceso a tu red local)

http_access deny all
(deniegas el acceso al resto de la red)

httpd_accel_host virtual

httpd_accel_port 0
(habilitas cache acelerada para cualquier puerto)

http_accel_with_proxy on

Y todas las demás opciones las dejas como vienen por defecto.

En los clientes, solo comentar que en cada una de las aplicaciones que utilices de cara a internet (los proxies son también conocidos como firewall de aplicación), habrá que configurar como proxy el que acabas de configurar.

En el firefox sería:

Edición - Preferencias - Avanzadas - Proxies
Aquí, marcas la casilla de "Configuración manual del proxy" y en la casilla
"Proxy HTTP" pones la dirección IP y como puerto el 3128

Saludos.

---

### Post by kha0s101 on 2008-03-15
[COLOR="DarkGreen"]UHHH no vi este pedazo de respuesta!!! Gracias!!!

Me pongo con esto y cuento que me pasó.

De nuevo, muchas gracias.[/COLOR]

---

### Post by kha0s101 on 2008-03-15
[COLOR="DarkGreen"]Lamentablemente, el proceso no ha funcionado. EL Squid me tira error y se cierra luego de instalado. Hice algún avance que comento [aquí]("http://ubuntuforums.org/showthread.php?t=724798") pero todavía la solución me esquiva.

Muchas gracias por una explicación tan completa. Volveré a intentarlo porque supongo que algo me faltó hacer para tener problemas.

Saludos.[/COLOR]

---

