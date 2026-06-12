---
title: "[SOLVED] 2º Instalacion de Ubuntu 7.10 AMD64 - Mismo Problema: GNOME_FastUserSwitchAp"
date: 2007-11-26
forum: Argentina Team
---

### Post by BiTFx on 2007-11-26
Hola gente, de vuelta con otro problema:

I**nstalé dos veces Ubuntu 7.10 AMD64** (ya tenia Windows XP en la primera partición, y lo sigo manteniendo)  porque despues de instalar la primera vez falló al otro día (la pasé espectacular el día sabado probándolo):

**1º:**
Instalé la placa nvidia, unos codecs, compiz fusion, conexion compartida a internet y otras aplicaciones y todo andaba muy bien, luego cuando arranqué aparecían muchas lineas de comando (como chequeos) y un error con GNOME_FastUserSwitch (**El panel ha encontrado un problema mientras cargaba OAFIID: GNOME_FastUserSwitchApplet ¿Desea borrar la miniaplicación de suconfiguración?**) le puse que si y no se arregló. el sistema tardaba como 10 minutos en arrancar y mostrar todo el escritorio, antes de eso, no puedo abrir nada...

**2º**
Asi que instalé todo Ubuntu 7.10 AMD64 de nuevo, eliminé las particiones donde estaba instalado originalmente y las cree de nuevo (desde 0 pero aún con Windows Xp en la primera partición). 

Se instaló perfecto, como la primera vez,  y a la segunda vez que arranqué Ubuntu, sin haber instalado nada, solo la placa nvidia, la conexion a internet (y un script para compartirla, ya que tengo 2 placas de red y una pc con win xp solamente), ya que no sabía que diablos era lo que hice mal la primera vez, y me aparece el mismo error y el mismo cartel, así que esta vez seleccioné que NO Borre la miniaplicación.

Probé reinstalando los applets:

**sudo aptitude install gnome-applets**

Me salió que 0 paquetes se instalaron, o sea, que no hubieron cambios, entonces probé Re instalar:

**sudo aptitude reinstall gnome-applets**

y reinstaló 1 paquete (ya que al tercer reinicio le puse que borrara la miniaplicación) y ya no apareció mas lo de GNOME_FastUserSwitchApplet.

**Con esto NO se arregló el problema, así que no se que hacer**, en estos momentos **solo tengo instalada la placa nvidia, creada la conexion a internet (speedy) y utilicé un script para poder compartir internet con con una pc con Windows XP** (pero no lo puse para que se cargara al inicio), si hace falta pongo el script, tal vez ahí he modificado algo que no debía, o sea, Ubuntu está con lo que instalé al principio y aun así falla.

El arranque demora unos 10 minutos hasta que aparece el escritorio con los íconos y la barra superior e inferior, y cada vez que abro alguna aplicacón se demora bastante en abrir, cuando instalé por primera vez todo anduvo espectacular, ahora no se ke pasó y siempre aparece al arrancar la pantalla negra con los chequeos donde al final de cada línea, alineado a la derecha aparece **[Ok]**

Gracias y espero que puedan ayudarme.

*Espero no me recomienden usar la versión de 32 bits, la de 64 debería andar bien no (tengo la verion Desktop y DVD)?.*

**Mi PC**: Placa Madre M2NPV-VM, Video NVIDIA GeForce 6150 (on board), Procesador AMD64 Athlon X2 3600+, **1 Gb** de Ram, Disco Rígido de** 250 Gb** Sata 2 

Si falta algo me avisan para agregar, me tomo unos mates y de paso un respiro...

---

### Post by BiTFx on 2007-11-26
Hola, reinstalé Ubuntu, e instalé nvidia, configuré internet, habilité compiz fusion y hasta acá todo bien, **creo ke el error fue el SCRIPT para compartir internet**, aun no lo he hecho (y creo ke mejor no comparto la conexion hasta asegurarme que sea un script confiable para esta version) y todo anda de mil maravillas en una resolucion de 1024 x 768.
 
Les dejo todo el documento del script por si alguien le encuentra el "posible" error, les comento que las 2 veces anteriores que lo probé, luego me falló ubuntu y no pude hacerlo andar bien (por eso tuve ke reinstalar 2 3 veces con esta Ubuntu), tampoco me andubo la conexion compartida:
 
------------------------------------------------------------------
 
**Compartir conexión a internet en linux (compatible con Windows XP)**

Enviado por mober el Mié, 30/11/2005 - 02:30 Web, plugins, cortafuegos y proxies 

Muchas veces tenemos en casa más de un PC que accede a través del nuestro a internet con la conexión compartida de windows xp, y queremos hacer lo mismo con linux para que los demás puedan seguir conectandose a internet mientras usemos linux.

Doy por supuesto que ya teneis configurado los 2 dispositivos de red, uno conectado a la red local y otro a internet (para el ejemplo supondremos que nuestro pc tiene en la red local la ip 192.168.0.1 y mascara de subred 255.255.255.0)
La mejor manera es crear un script que se cargue al iniciar el sistema y que configure las reglas de iptables, que es un firewall integrado en el kernel que también permite el enroutamiento de conexiones.

Tenemos que hacer lo siguiente:

1.- Creamos un nuevo archivo que vamos a editar:
$ sudo gedit /etc/init.d/iptablesconf 
2.- Ahora copiamos y pegamos el siguiente script en el editor de texto, sólo tenemos que modificar las 5 cadenas que están en negrita, donde pone eth1 y eth0 lo revisaremos para ver si efectivamente eth1 y eth0 son nuestros dispositivos de red conectados a internet y a la red local respectivamente.
Lo siguiente es por si queremos redigir cierto puerto a un ordenador de la red (que llamaremos pc2) local para que pueda por ejemplo usar el emule o tener activo un servidor ftp, etc.. , se supone que en el ejemplo redirigiremos en puerto 7778 tcp y 7779 udp al pc con la ip 192.168.0.2
Si no estamos interesados en redirigir puertos podemos borrar/comentar esas 3 variables.
 
#### SCRIPT DE CONFIGURACION DE IPTABLES ####
#!/bin/bash
# Dispositivo de red de internet
EXIF="eth0"
# Dispositivo de red local
INIF="eth1"
# Puertos tcp que se desean redirigir (separados por espacios)
#puertosTCP="7778"
# Puertos udp que se desean redirigir (separados por espacios)
#puertosUDP="7779"
# ip a la que se le redirigen los puertos
#pc2="192.168.0.2"
fail=0
[ -f /etc/default/rcS ] && . /etc/default/rcS
. /lib/lsb/init-functions
log_begin_msg "Aplicando Reglas de Firewall..."
## Borrado de reglas anteriores
iptables -F || fail=1
iptables -X || fail=1
iptables -Z || fail=1
iptables -t nat -F || fail=1
## Establecemos politica por defecto
iptables -P INPUT ACCEPT || fail=1
iptables -P OUTPUT ACCEPT || fail=1
iptables -P FORWARD DROP || fail=1
iptables -t nat -P PREROUTING ACCEPT || fail=1
iptables -t nat -P POSTROUTING ACCEPT || fail=1
# Marcar paquetes salientes con su ip de origen
iptables -t nat -A POSTROUTING -o $EXIF -j MASQUERADE || fail=1
# Reenvio de IP
echo 1 > /proc/sys/net/ipv4/ip_forward || fail=1
# Aceptar paquetes para reenviar procedentes de la red local
iptables -A FORWARD -i $INIF -o $EXIF -j ACCEPT || fail=1
# Aceptar paquetes para reenviar procedentes de internet de conexiones ya establecidas
iptables -A FORWARD -i $EXIF -o $INIF -m state --state RELATED,ESTABLISHED -j ACCEPT || fail=1
##Se redirigen los puertos configurados arriba
for puerto in $puertosTCP
do
iptables -A FORWARD -i $EXIF -o $INIF -p tcp --dport $puerto -j ACCEPT || fail=1
iptables -t nat -A PREROUTING -i $EXIF -p tcp --dport $puerto -j DNAT --to $pc2:$puerto || fail=1
done
for puerto in $puertosUDP
do
iptables -A FORWARD -i $EXIF -o $INIF -p udp --dport $puerto -j ACCEPT || fail=1
iptables -t nat -A PREROUTING -i $EXIF -p udp --dport $puerto -j DNAT --to $pc2:$puerto || fail=1
done
# Se muestran los resultados
log_end_msg $fail
if [ $fail -eq 0 ]
then
log_success_msg "Verifique que lo que se aplica con: iptables -L -n."
else
log_warning_msg "Se ha producido un error al aplicar alguna de las reglas"
fi
#### FIN SCRIPT DE CONFIGURACION DE IPTABLES ####

3.- Guardamos los cambios y le damos permisos de ejecucion:
$ sudo chmod -v 755 /etc/init.d/conexioncompartida
el modo de «iptablesconf» cambia a 0755 (rwxr-xr-x) 
Lo ejecutamos:
$ sudo /etc/init.d/conexioncompartida 
si todo ha ido bien veremos este mensaje:
* Aplicando Reglas de Firewall... [ ok ]
* Verifique la reglas: iptables -L -n.
Ahora utilizamos el siguiente comando para que script se cargue cada vez que arranque el sistema:
$ sudo update-rc.d conexioncompartida start 20 2 . 
#### ATENCIÓN AL PUNTO DEL FINAL, HAY QUE PONERLO ####
Adding system startup for /etc/init.d/iptablesconf ...
/etc/rc2.d/S20iptablesconf -> ../init.d/iptablesconf 

4.- Ahora podemos probar si todo funciona, nos vamos a los otros PCs y configuramos la red con ips estaticas (por ej 192.168.0.2 , 192.168.0.3 , etc..) y su correspondiente mascara de subred (255.255.255.0 para el ejemplo) utilizamos como puerta de enlace el pc que comparte la conexión (192.168.0.1 en el ejemplo) y como servidores dns utilizamos los mismos que tenga configurados el pc que da acceso a internet, que podemos verlos utilizando
$ cat /etc/resolv.conf 
Ahora si todo ha ido bien debería funcionar internet en los otros PCs una vez configurados.

 
---------------
 
No me rpegunten Copyright porque lo guardéen un txt y no se de donde salió.

---

### Post by faktorqm on 2007-11-28
che yo aca mismo postie un script para compartir la conexion mas facil que contar 1-2-3 sin tanto espamento y en 3 lineas. 

[http://ubuntuforums.org/showthread.php?t=619358](http://ubuntuforums.org/showthread.php?t=619358)

espero que te sirva salu2! OJO con la configuracion de las placas fijate bien cual es eth0 cual eth1.

---

### Post by BiTFx on 2007-11-28
> **faktorqm said:**
> che yo aca mismo postie un script para compartir la conexion mas facil que contar 1-2-3 sin tanto espamento y en 3 lineas. 
 
[http://ubuntuforums.org/showthread.php?t=619358](http://ubuntuforums.org/showthread.php?t=619358)
 
espero que te sirva salu2! OJO con la configuracion de las placas fijate bien cual es eth0 cual eth1.
 
Gracias, ya puse una pregunta en el post que me sugeris.

---

