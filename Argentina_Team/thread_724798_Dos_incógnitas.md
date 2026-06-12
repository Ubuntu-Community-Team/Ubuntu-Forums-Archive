---
title: "Dos incógnitas"
date: 2008-03-15
forum: Argentina Team
---

### Post by kha0s101 on 2008-03-15
[COLOR="DarkGreen"]Hola.

Estoy con dos situaciones donde necesito su ayuda.

**SITUACION 1**. 

Tengo 2 pcs conectadas con un cable cruzado. Una (PC1) conectada al "alfajor del diablo" Huawei MT810 para servir internet a la otra (PC2).

Ambas tienen Ubuntu 7.10 Haciendo ping de una a otra, se "ven" pero es todo lo que consigo. No puedo hacer que la 2º pc se conecte a internet. 


PC 1
eth0 inet addr:192.168.0.1  Bcast:192.168.0.255  Mask:255.255.255.0
          
PC 2
eth0 inet addr:192.168.0.2  Bcast:192.168.0.255  Mask:255.255.255.0
          
Se que no es problema de hard porque bajo güindou$ se ven e inclusive si PC1 arranca en güindou$ PC2 navega sin problemas.



**SITUACION 2**

Necesito restringir un usuario bastantes privilegios ya que entre otras cosas, una de las pcs tiene información de trabajo y no quiero que nadie pueda acceder a ella. He creado un usuario específico para los invitados pero no encuentro su fstab para inhibir algunas particiones del disco rigido y evitar que acceda a esa información.

Toda ayuda es bienvenida. Muchas gracias.

Saludos.[/COLOR]

---

### Post by newtonfn on 2008-03-15
**Situación 1:**

La compartición de internet es algo que se debe configurar. Se puede hacer desde la linea de comando configurando correctamente iptables, pero honestamente no se hacerlo manualmente.

Yo instalé un firewall llamado Firestarter (podes encontrarlo en los repositorios) que en su configuración te permite precisamente configurar la compartición de internet.

Nunca lo he usado con un modem USB, pero imagino no habrá mayores problemas para configurarlo.

Con respecto a la PC2, deberás configurar además, que el default gateway sea 192.168.0.1 para que funcione.

**Situación 2**

Hasta donde se, el fstab no es por usuario, sino que es general para todos el sistema. Se me ocurren varias alternativas. La primera es quitar los discos del fstab y en el usuari que debe acceder a ellos montarlos por un script o manualmente cuando los necesites.

Sin embargo me parece más practico hacer buen uso de los permisos. O sea, tener siempre montado el disco, pero a aquellos archivos y/o directorios que son "restringuidos" quitarles los permisos a los usuarios no autorizados

O sea, yo haría lo siguiente.
Si solo quiero que un pequeño gurpo de usuarios acceda al directorio /mnt/work, cambio el owner de la carpeta a root:trabajo (por ejemplo) y los permisos para que solo el owner y el group puedan verlo, y a others no tenga permiso para nada (basicamente, rwxrwx---)

Previamente cree un grupo llamado trabajo usando el comando addgroup.

Finalmente, aquellos usuarios que debe poder ver esos archivos, los agrego al grupo trabajo (puedo hacerlo usando el comando usermod)

De esta manera, cualquier usuario que no pertenezca al grupo "trabajo" no podrá acceder a los archivos que qures protejer.

Admito que no fui muy detallista en la explicación, pero creo haber transitido una idea, que con un poco de investigación podrás llevar a cabo, sin embargo, si en algo no supe explicarme o necesitas una pequeña ayuda, no dudes en preguntar nuevamente en este post.

Saludos,
Fernando

---

### Post by kha0s101 on 2008-03-15
[COLOR="DarkGreen"]Hola. Sobre el tema de la red, anduve dando vueltas, hice otras pruebas y al fin y al cabo, dejé las pcs configuradas así:

PC1 eth0 192.168.0.1   Bcast 192.168.0.255   netmask 255.255.255.0

PC2 eth0 192.168.0.2   Bcast 192.168.0.255   netmask 255.255.255.0
gateway  192.168.0.1

Sigo casi igual que antes, a excepción que puedo hacer ping a [www.google.com](www.google.com) y tengo respuesta, sin embargo no puedo navegar :mad:

Probé con Firestarter y no hubo caso. También con Squid según el procedimiento que me indicó newtonfn [aquí]("http://ubuntuforums.org/showthread.php?p=4523539#post4523539")
 pero tampoco funcionó

Seguí los pasos indicados en [ésta página]("http://byroncervantes.wordpress.com/2007/12/10/compartir-internet-ubuntu-710-gutsy-gibbon/") hasta donde se debe escribir el script. Sin embargo tampoco anda. 

En otra prueba, inicié Xp desde PC1 y PC2, desde Ubuntu 7.10 navega fantásticamente. No soy muy ducho en estas cosas, pero la verdad me tiene intrigado cual pueda ser la falla :confused::confused:

Estoy investigando el tema de configuración de permisos de usuarios; creo que es justo lo que buscaba. Gracias!

Saludos.
[/COLOR]

---

### Post by gmunioz on 2008-03-15
Hola kha...:
Lee esto, puede que te sirva:
Parámetros y configuración adecuados a tus valores:

# You may specify multiple socket addresses on multiple lines.
# Default: http_port 3128
[B]http_port 3128
http_port 8080[/B]

Si deseas incrementar la seguridad, puedes vincula el servicio a una IP que solo se pueda acceder desde la red local. Considerando que el servidor utilizado posee una IP 192.168.0.1, puedes hacer lo siguiente:

# You may specify multiple socket addresses on multiple lines.
# Default: http_port 3128
[B]http_port 192.168.0.1:3128
http_port 192.168.0.1:8080[/B]

Parámetro cache_mem.
El parámetro cache_mem establece la cantidad ideal de memoria para lo siguiente:
Objetos en tránsito.
Objetos frecuentemente utilizados (Hot).
Objetos negativamente almacenados en el caché.

De modo predefinido se establecen 8 MB. Si se posee un servidor con al menos 128 MB de RAM, 16 MB es el valor para este parámetro:
**cache_mem 16 MB**

Parámetro cache_dir:
El parámetro cache_dir se utiliza para establecer que tamaño se desea que tenga el caché en el disco duro para Squid. De modo predefinido Squid utilizará un caché de 100 MB, de modo tal que encontrará la siguiente línea:
cache_dir ufs /var/spool/squid 100 16 256
Mientras más grande sea el caché, más objetos se almacenarán en éste y por lo tanto se utilizará menos el ancho de banda. La siguiente línea establece un caché de 700 MB:
**cache_dir ufs /var/spool/squid 700 16 256**
Los números 16 y 256 significan que el directorio del caché contendrá 16 directorios subordinados con 256 niveles cada uno.

Controles de acceso.
Las Listas de Control de Acceso definen una red o bien ciertas máquinas en particular. A cada lista se le asignará una Regla de Control de Acceso que permitirá o denegará el acceso a Squid.
Listas de control de acceso, se establecen con la siguiente sintaxis:
acl [nombre de la lista] src [lo que compone a la lista]

En tu caso puedes establecer una lista de control de acceso que abarque a toda la red local, basta definir la IP correspondiente a la red y la máscara de la sub-red. 
 
**acl todalared src 192.168.0.0/255.255.255.0**


Reglas de Control de Acceso.

Las Reglas de control de Aceso definen si se permite o no el acceso hacia Squid. Se aplican a las Listas de Control de Acceso. Deben colocarse en la sección de reglas de control de acceso definidas por el administrador, es decir, a partir de donde se localiza la siguiente leyenda:

# INSERT YOUR OWN RULE(S) HERE TO ALLOW ACCESS FROM YOUR CLIENTS

La sintaxis básica es la siguiente:

http_access [deny o allow] [lista de control de acceso]

Considerando como ejemplo que dispones de una red 192.168.0.0/255.255.255.0, si se desea definir toda la red local, utilizaras la siguiente línea en la sección de Listas de Control de Acceso:

**acl todalared src 192.168.0.0/255.255.255.0**

Listas de Control de Acceso: definición de una red local completa

# Recommended minimum configuration:
[B]acl all src 0.0.0.0/0.0.0.0
acl manager proto cache_object
acl localhost src 127.0.0.1/255.255.255.255
acl todalared src 192.168.0.0/255.255.255.0[/B]

A continuación procedes a aplicar la regla de control de acceso:
**http_access allow todalared**

Para crear el directorio cache, en modo consola ejecuta:
**sudo squid -z**

Cualquier error al inicio de Squid solo significa que hubo errores de sintaxis, errores de teclado o de las rutas hacia los archivos de las Listas de Control de Acceso.

En caso de errores graves que no permiten iniciar el servicio, examinar el contenido del archivo /var/log/squid/squid.out ejecutando en consola:

**less /var/log/squid/squid.out**

Ajustes para el muro corta-fuegos.

Re-direccionamiento de peticiones a través de iptables y Firestarter.

Para dar salida transparente hacia Internet a ciertos servicios y/o al mismo tiempo re-direccionar peticiones hacia servicio HTTP para pasar a través del el puerto donde escucha peticiones Squid (8080), de modo que no haya salida alguna hacia alguna hacia servidores HTTP en el exterior sin que ésta pase antes por Squid, los protocolos HTTPS, FTP, GOPHER ni WAIS, deben ser filtrados a través del NAT.

El re-direccionamiento se hace a través de iptables. Suponiendo que la red local se accede a través de una interfaz eth1, el siguiente esquema ejemplifica un re-direccionamiento:

**sudo iptables -t nat -A PREROUTING -i eth1 -p tcp --dport 80 -j REDIRECT --to-port 8080**

Lo anterior, que requiere un guión de cortafuegos funcional en un sistema con dos interfaces de red, hace que cualquier petición hacia el puerto 80 (servicio HTTP) hecha desde la red local hacia el exterior, se re-direccionará hacia el puerto 8080 del servidor.

Utilizando Firestarter, la regla anteriormente descrita se añade en el archivo /etc/firestarter/user-post.
sudo gedit /etc/firestarter/user-post
y se agrega la línea
**iptables -t nat -A PREROUTING -i eth1 -p tcp --dport 80 -j REDIRECT --to-port 8080**

Tambien puedes intentar, que parece mas sencillo de implementar:

Compartir la conexión con Iptables

Iptables funciona de forma parecida a las reglas de acceso del proxy squid, para compartir la conexión a internet debes "Hacer NAT de tu red local", 

Hacer NAT/MASQUERADE de una red, es simplemente enmascarar las ip's de dicha red con otra diferente, en tu caso la maquina cuya ip es 192.168.0.1 le sirve de pasarela de otra maquina cuya ip es 192.168.0.2. 
Hacer NAT de esta última maquina, significa que de cara al exterior las conexiones las estará haciendo 192.168.0.1, aunque sea 192.168.0.2, la que esté accediendo al exterior.


La forma de utilizar iptables, es ir escribiendo regla por regla, recordando la misma limitación del orden de las reglas que tenías en el proxy. 
Como estas reglas se guardan en memoria, perdiéndose cuando apagas el ordenado, para evitarlo, lo que puedes hacer es escribir en orden las reglas en un script, el cual puedes ejecutar en el inicio del sistema
Para ello, editas un fichero de texto, por ejemplo:

/etc/init.d/firewall
Donde pondras esto teniendo en cuenta que tu red local es del tipo 192.168.0.0 y sales a Internet a través de la interfaz nas0. 

modprobe iptable_nat 
iptables -t nat -A POSTROUTING -s 192.168.1.0/24 -o nas0 -j MASQUERADE
echo 1 > /proc/sys/net/ipv4/ip_forward

Una vez que lo tienes, le das permisos de ejecución:

sudo chmod +x /etc/init.d/firewall


Y lo pones en el arranque del sistema:

sudo ln -s /etc/init.d/firewall /etc/rc2.d/S99firewall
sudo ln -s /etc/init.d/firewall /etc/rc3.d/S99firewall
sudo ln -s /etc/init.d/firewall /etc/rc4.d/S99firewall
sudo ln -s /etc/init.d/firewall /etc/rc5.d/S99firewall

Configuración del cliente
En el cliente de tu red local, lo único que hay que hacer es poner como puerta de enlace predeterminada (o gateway), la ip de la maquina que acabas de configurar, que ya lo has hecho.

Saludos

---

### Post by newtonfn on 2008-03-16
Hum... si lograste hacer ping a google.com no se por qué tenes problemas para navegar. El hecho de hacer ping a google significa que los DNS estan bien configurados porque en caso contrario no sabría resolver la URL con el IP (algo que me olvide de decirte antes, pero por si las dudas te comento ahora es que debes copiar los dns que tu ISP te da en /etc/resolv.conf) y por otro lado si te responde al ping significa que la red está bien configurada y estas enviando y recibiendo paquetes.

Al menos yo nunca me enfrenté al poder hacer un ping y no poder navegar. Espero logres resolver tu problema... lamentablmente yo no tengo mas ideas :(

(Un comentario, el procedimiento para usar Squid no te lo di yo, asi que el reconocimiento por ello debe ir a otra persona.)

---

