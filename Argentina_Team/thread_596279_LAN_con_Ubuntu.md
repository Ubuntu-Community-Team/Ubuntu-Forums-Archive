---
title: "LAN con Ubuntu"
date: 2007-10-29
forum: Argentina Team
---

### Post by LaHire on 2007-10-29
Saludos a todos!

primero que todo, me siento medio tonto preguntando estas cosas, (principalmente porque debería saber hacerlo! trabajo de esto! :lolflag:)

En fin, bueno, perdón por la pregunta tonta xD


[U]Situación:
[/U] Tengo dos pc's. una Dekstop con Ubuntu 7.04, rota (recompilé el kernel una vez y explotó todo a 10 [pársecs]("http://es.wikipedia.org/wiki/P%C3%A1rsec") a la redonda), así que le corro un Live Cd de Ubuntu 7.10

y la otra, una notebook, con ubuntu 7.10 y windows Vista (Home Premium), en dual boot.


_Objetivo:_
Crear una red (temporal) de pc a pc (o sea, tengo el cable cruzado listo y andando (lo cable-testié :P)) entre  la desktop y la notebook (usando Ubuntu en ambas)

[U]Problema:
[/U]Nunca configuré una red en Ubuntu, (digamos: dependo del Roaming y de el DNS de mi modem router (que no quiero meter en la red, solo es algo de pc a pc  sin nada mas que un cable cross-over en el medio)) así que no puedo proceder correctamente

hice unas cosas...
como...poner a ambas pc en modo "ip fija", con dos direcciónes (por poner: 192.168.0.100 y (...)0.10) y en la mísma mascara. Ahora...como las pongo en el mismo workgroup?, haciendo click por ahí (siempre desde el daemon de red en Preferencias > Administración), "encontré" un "Nombre del equipo" y "Dominio"

probé tocar ahí, y las puse en el mismo dominio...pero nada

ahora bien, mi pregunta: ¿qué estoy haciendo mal?

si, soy n00b, lo confieso.-

gracias desde ya!

---

### Post by Hernán-Amaya on 2007-10-29
IP pc1: 192.168.0.1
IP pc2: 192.168.0.2

con eso se tendrian que ver las dos pcs

proba entrando en Sistema /  Administración / Herramientas de red

y ahí hace un ping a la otra maquina y deberías ver que hay conexión entre ellas

para compartir internet entre las dos te conviene usar Firestarter (en la pc que tiene internet)

proba y contanos como te fue

suerte!!!!!!!!

---

### Post by JanusDC on 2007-10-29
Con las IPs que le pusiste ya se deberían estar viendo. Hacé un ping y te vas a dar cuenta.
Si querés poder pasar archivos o loguearte desde una a otra, tenés que instalar ssh para levantar un "servidor" ssh.
Hacé esto desde la consola:
sudo apt-get install ssh
sudo /etc/init.d/ssh start
Luego, desde la otra máquina podrás crear una conexión a la que tiene el servidor ssh corriendo.
Salu2

---

### Post by faktorqm on 2007-10-30
Hola, en una pc, abri un terminal y pone:

```
ifconfig eth0 192.168.0.1 netmask 255.255.255.0
```

sino anda mandale sudo adelante.

En la otra pc, abris un terminal y pones:

```
ifconfig eth0 192.168.0.2 netmask 255.255.255.0
```

we, ahora segui este tutorial que lo escribi yo, asi que si tenes dudas me avisas.

Tutorial básico de samba para compartir carpetas e impresoras en una red hogareña.

Consideraciones previas: Este tutorial está orientado exclusivamente a aquellos usuarios que son nuevos y principiantes en entornos GNU/Linux, para las distribuciones Ubuntu, Kubuntu y Xubuntu. Por lo tanto, este tutorial omite en reiteradas oportunidades aspectos de configuración avanzados y otro tipo de dificultades que no se consideran necesarias para una red hogareña ni para usuarios principiantes, así como aspectos técnicos y referidos a normas internacionales.
También se considera que la red hogareña posee buen funcionamiento, buen mantenimiento y se ha utilizado anteriormente en otros sistemas operativos sin dificultades.

Introducción acerca del protocolo SMB:

SMB (Server Message Block) es un protocolo creado en 1985 por IBM (International Business Machines). Algunas veces es referido también como CIFS (Common Internet File System, [http://samba.org/cifs/](http://samba.org/cifs/)) tras ser renombrado por Microsoft en 1998. Entre otras cosas, Microsoft añadió al protocolo soporte para enlaces simbólicos y duros así como también soporte para ficheros de gran tamaño. Por mera coincidencia esto ocurrió por la misma época en que Sun Microsystems hizo el lanzamiento de WebNFS (una versión extendida de NFS, Network File System, [http://www.sun.com/software/webnfs/overview.xml](http://www.sun.com/software/webnfs/overview.xml)).

SMB fue originalmente diseñado para trabajar a través del protoclo NetBIOS (Network Basic Input/Output System), el cual a su vez trabaja sobre NetBEUI (NetBIOS Extended User Interface, o Interfaz de Usuario Extendida de NetBIOS), IPX/SPX (Internet Packet Exchange/Sequenced Packet Exchange, o Intercambio de paquetes interred/Intercambio de paquetes secuenciales) o NBT (NetBios over TCP), aunque también puede trabajar directamente sobre TCP/IP (Transfer Control Protocol/Internet Protocol, o Protocolo de Control de Transmisión/Protocolo de Internet)

Introducción acerca de Samba:

SAMBA ([http://www.samba.org/](http://www.samba.org/)) es un conjunto de programas, originalmente creados por Andrew Tridgell y actualmente mantenidos por The SAMBA Team ([http://www.samba.org/samba/team.html](http://www.samba.org/samba/team.html)), bajo la Licencia Publica General GNU ([http://www.gnu.org/](http://www.gnu.org/)), y que implementan en sistemas basados sobre UNIX el protocolo SMB. Sirve como reemplazo total para Windows NT, Warp, NFS o servidores Netware.

Este protocolo permite compartir varios recursos diferentes:
El acceso a las impresoras conectadas fisicamente a las maquinas.
El acceso a los directorios compartidos.

El paquete SAMBA incluye utilidades para controlar el acceso de los archivos con la misma soltura que un WindowsNT.
Veremos mas adelante como configurarlo en detalle, pero es posible:

    * Proteger por contraseña el acceso a un directorio compartido.
    * Proteger con una contraseña personificada para cada usuario, y dotar de permisos de acceso individualizados.

Dos o tres demonios se encargan de ofrecer los servicios de la conjunto de aplicaciones del Samba. El primero es el smbd,
el segundo de ellos es el nmbd, y el tercero es el winbindd.

SMBD es el demonio que se encarga de los recursos compartidos: ficheros, impresoras, etc, pero también del control del acceso a los recursos. Gestiona los permisos de los diferentes clientes una vez que estos han sido identificados.

NMBD se ocupa de anunciar servicios. Es decir, se encarga de informar a las maquinas presentes en la red sobre cuales son los recursos disponibles. Este demonio maneja también la resolución de nombres de NetBIOS (Network Basic Input/Output System). Puede para ello comunicarse con un servidor WINS (Windows Internet Naming Service) presente en la red.

WINBINDD es un demonio que se inicia cuando Samba es miembro de un dominio Windows NT4 o ADS o cuando tiene relaciones de confianza con otro dominio. Éste demonio se referirá al archivo smb.conf para buscar la presencia de los parametros idmap UID (User Identifier) y GID (Group Identifier). Si son encontrados, winbindd utilizará los valores especificados para la asignación UID y GID. Si estos parámetros no existen, winbindd se inciará pero no será capaz de asignar ningún UID ni GID.

Nota: La resolución de nombres consiste en obtener una equivalencia entre la dirección IP de la LAN (Local Area Network o Red de Área Local) y el nombre de la máquina.

Hasta aquí hemos repasado un poco de teoría, ahora vayamos a la práctica.

Instalación de los paquetes correspondientes:

Debemos instalar desde los repositorios los siguientes paquetes para asegurarnos de poseer todas las herramientas para compartir archivos e impresoras de manera correcta:

sudo apt-get install samba samba-common samba-doc-pdf gsambad

Los paquetes samba y samba-common son los básicos de samba, samba-doc-pdf como su nombre lo indica es la documentación del mismo en formato PDF (Portable Data Format) y gsambad es una utilidad de configuración gráfica de samba. Existen varios front-ends para samba, pero en este tutorial no nombraremos ninguno.

Una vez terminado el proceso (exitoso) de instalación, procedemos a configurar samba para poder comenzar a compartir.

Samba utiliza un único archivo de configuración, llamado smb.conf, sito en /etc/samba/ que posee todas las entradas de configuración en modo texto, al estilo de los viejos archivos .ini de Windows.

Lo primero que tenemos que hacer, independientemente de qué sistemas operativos tengamos en las computadoras, es generar una copia de back-up del archivo de configuración de samba, y luego establecer un grupo de trabajo (el mismo en todas) y un nombre para cada computadora (distinto en todas).

Para lograr lo primero hacemos:

sudo cp /etc/samba/smb.conf /etc/samba/smb_old_0.conf

El número se debe a que probablemente debamos configurar en reiteradas oportunidades este archivo, por lo tanto debemos generar distintos back-up's del mismo por razones de seguridad, de esta manera sabremos que el 0 (cero) es el predeterminado de instalación.

Para establecer el grupo de trabajo simplemente consta en ponerse de acuerdo sobre el nombre del mismo y poner el mismo en todas las computadoras, tengan el sistema operativo que tengan.

Ahora vamos a compartir una carpeta de ejemplo, la crearemos por una cuestión de comodidad en /home/

sudo mkdir /home/publico

Una vez creada la carpeta, debemos asignar los permisos necesarios para que los otros usuarios puedan acceder:

* Si queremos que los usuarios puedan escribir sobre la carpeta compartida ponemos:

sudo chmod 755 /home/publico

* Si queremos que SOLO PUEDAN LEER (no podrán escribir ni modificar ni borrar archivos) ponemos:

sudo chmod 555 /home/publico


Ahora bien, hecho esto pasamos a configurar directamente el archivo smb.conf. Por ahora, vamos a borrar completamente el contenido del archivo y vamos a copiar y a pegar exactamente esto:

para editar el archivo desde la interfaz grafica: sudo gedit /etc/samba/smb.conf

para editar el archivo desde la consola (terminal): sudo nano /etc/samba/smb.conf

[global]
workgroup = migrupo
security = SHARE
[compartido]
path = /home/publico
read only = no
guest ok = yes


Como verán, el archivo es bastante autocomprensible, pero LUEGO DE GUARDARLO vamos a analizarlo detalladamente para evitar confusiones.

Las palabras puestas entre corchetes ("[" y "]") significan lo que se llama una llave. Una llave sirve para establecer diferentes cosas. En este caso, utilizaremos 2 llaves, la "global" y la "compartido". La llave global establece directivas sobre como debe comportarse samba. En este caso, le especificamos a samba como se llama el grupo de trabajo.
La otra llave (compartido) es una llave que cada uno puede establecer su nombre como le parezca, es decir, cada llave que se encuentre abajo de global será el nombre de como verán los otros usuarios de la red un recurso compartido.
En este caso cuando alguien se conecte a nuestra PC verá un recurso compartido llamado "compartido", y no necesariamente se tiene que llamar igual que la carpeta ("publico").
De esta forma, si yo cambio el archivo smb.conf de la siguiente manera:

[global]
workgroup = migrupo
security = SHARE
[ejemplo]
path = /home/publico
read only = no
guest ok = yes

los otros usuarios de la red verán un recurso compartido llamado ejemplo.

Si quiero compartir mas de una carpeta, en este ejemplo llamada datos, puedo hacer lo siguiente:

[global]
workgroup = migrupo
security = SHARE
[publico]
path = /home/publico
read only = no
guest ok = yes
[segunda]
path = /media/datos
read only = yes
guest ok = yes

y los nombres de los recursos compartidos serán "publico" y "segunda".

Dicho esto, nos detenemos sobre las claves.

"workgroup": Esta clave define en que grupo de trabajo vamos a encontrarnos con los otros PC's de la red. 
Todos los PC's de la red deben tener el mismo nombre de grupo de trabajo, de lo contrario, no podrán compartir los recursos de red.

"security": Esta clave nos permite elegir entre compartir carpetas sin contraseña, o sea, a nivel servicio, o a nivel usuario, mediante la utilizacion de un usuario y una contraseña.

"path": Esta clave se utiliza para indicarle a samba la ruta de la carpeta que queremos compartir, independientemente del nombre que elijamos para compartirla. Recordar que para compartir una carpeta, primero debemos asegurarnos de poseer los permisos necesarios para efectuar las operaciones que consideremos oportunas. Si en una carpeta tenemos acceso de sólo lectura, y compartimos la carpeta para que los otros usuarios de la red puedan cambiar el contenido, no podrán debido a que la carpeta no tiene los permisos requeridos.

"read only": Como su nombre lo indica, esta clave establece si la carpeta compartida debe ser de solo lectura o no. Los valores posibles son "no" y "yes".

"guest ok": Esta clave es para habilitar lo que se llama el invitado, es para acceder sin usuario a una carpeta, y podamos verla. También supone un riesgo de seguridad esta clave, pero como estamos en un red hogareña, por el momento no nos interesa.

Bueno, retomando el hilo, hasta ahora hemos creado una carpeta, le asignamos los permisos, armamos el archivo de configuración, ahora hay que comprobar si el archivo de configuración es correcto.

Para probar la configuración, existe un programa llamado TESTPARM que lee el archivo de configuración y reporta cualquier error de sintaxis. Cualquier parámetro de configuración aún no establecido será ajustado a su valor por defecto. Recuerde que su archivo de configuración puede estar sintácticamente correcto pero no apropiado para su uso, por ejemplo, si no creamos la carpeta "publico" en /home/ testparm EN NINGÚN CASO devolverá código de error.

Para estar seguros de que todo ande bien, adjunto la salida de testparm en mi computadora. Si no es idéntica la salida, no importa, cambia dependiendo de cada configuración.

$testparm

Load smb config files from /etc/samba/smb.conf
Processing section "[compartido]"
Loaded services file OK.
Server role: ROLE_STANDALONE
Press enter to see a dump of your service definitions

[global]
        workgroup = MIGRUPO
	security = SHARE
[compartido]
        path = /home/publico
        read only = No
        guest ok = Yes

Ahora bien, MODIFIQUÉ A PROPÓSITO el archivo smb.conf para que vean como testparm nos devela a donde se encuentra el error. 
Le sustraí la última letra a la primera clave, "workgroup" fue reemplazado por "workgrou" y ésta es la salida generada por testparm:

$testparm

Load smb config files from /etc/samba/smb.conf
Unknown parameter encountered: "workgrou"
Ignoring unknown parameter "workgrou"
Processing section "[compartido]"
Loaded services file OK.
Server role: ROLE_STANDALONE
Press enter to see a dump of your service definitions

[global]
	security = SHARE
[compartido]
        path = /home/publico
        read only = No
        guest ok = Yes

Fíjense cómo testparm nos avisa del error y si levantáramos el servicio con este archivo de configuración, ignoraría las palabras clave sintácticamente incorrectas, provocando esto el mal funcionamiento, debido a que no estamos presentes en ningún grupo de trabajo. 

Ahora debemos reiniciar el servidor samba para que tome los cambios propuestos, para esto hacemos:

sudo /etc/init.d/samba restart

Debemos tener una salida como esta:

 * Stopping Samba daemons...                                             [ OK ]
 * Starting Samba daemons...                                             [ OK ]

Con todo lo anterior deberíamos ser capaces de entrar desde un equipo con windows o linux a la carpeta /home/publico sin necesidad de tener nombre de usuario ni password:

    * Desde Windows colocamos en la barra de direcciones de alguna ventana: 

	\\<direccion>\publico

    * Desde Linux (que tenga instalado el paquete samba-client) abrimos una carpeta y colocamos en la barra de direcciones: 

	smb://<direccion>/publico/

donde <direccion> es "la IP privada" del equipo linux que contiene a la carpeta /home/publico. Desde sistemas operativos Windows también podemos acceder desde Entorno de red (o Mis sitios de red) por el explorador de Windows.

Bueno, espero que te haya servido. AVISA si hay que agregar algun paso o hay info que esta "bugeada", pero este tuto lo probe en 3 redes, asi que esta exento de error. Salu2!!!!!

---

