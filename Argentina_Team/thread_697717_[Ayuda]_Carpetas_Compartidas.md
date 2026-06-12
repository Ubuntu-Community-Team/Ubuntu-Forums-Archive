---
title: "[Ayuda] Carpetas Compartidas"
date: 2008-02-15
forum: Argentina Team
---

### Post by YOGUI on 2008-02-15
Buenas .
Soy nuevito en Ubuntu y estoy migrando de a poco mi Pc del laburo. El tema es que tengo que compartir algunos archivos con la red y no se como hacerlo. 
Tengo Ubuntu 7.10 y ya instalé los archivos de samba que me pedian en Sistema>Administración>Carpetas Compartidas, y agregué algunas carpetas a compartir. También puse el mismo grupo de trabajo que se usa en la red.
Como hago para ver esas carpetas desde otra terminal con WinXP?
En algo le estoy errando...
Gracias por por responder...

---

### Post by Mauro22 on 2008-02-16
Hola!


Las Pc estan dentro de la misma red (direccions ip) y dentro del mismo grupo de trabajo??


Ves las carpetas que compartis con el Xp e Ubuntu??

---

### Post by faktorqm on 2008-02-16
No encuentro el link de donde habia publicado esto......... asi que te lo pego aca.... lo escribi yo, espero que te sirva. No recuerdo si esta terminado, o si tiene algunas incoherencias, o si le faltan probar cosas, pero compartir vas a compartir ;) cualquier cosa preguntame. salu2!

Tutorial básico de samba para compartir carpetas e impresoras en una red hogareña

Consideraciones previas: Este tutorial está orientado exclusivamente a aquellos usuarios que son nuevos y principiantes en entornos GNU/Linux, para las distribuciones Ubuntu, Kubuntu y Xubuntu. Por lo tanto, este tutorial omite en reiteradas oportunidades aspectos de configuración avanzados y otro tipo de dificultades que no se consideran necesarias para una red hogareña ni para usuarios principiantes, así como aspectos técnicos y referidos a normas internacionales.
También se considera que la red hogareña posee buen funcionamiento, buen mantenimiento y se ha utilizado anteriormente en otros sistemas operativos sin dificultades.

Índice:
1.0- Introducción a samba.
1.1- El protocolo SMB.
1.2- Acerca de samba.
1.3- Composición del paquete SAMBA.
1.4- El archivo smb.conf.
1.5- Testparm, la utilidad de detección de errores de samba.
2.0- Compartir carpetas sin usuario ni contraseña.
3.0- Compartir carpetas utilizando usuario y contraseña.
4.0- FAQ (Preguntas frecuentes)
4.1- ¿Cómo hago para detener el servicio samba?
4.2- ¿Cómo hago para eliminar usuarios que creé?
4.3- ¡Mi Windows no me permite explorar el grupo de trabajo y estoy seguro de que hice correctamente este COMO!
5.0- Bibliografía.

1.0- Introducción a samba:

1.1- Introducción acerca del protocolo SMB:
SMB (Server Message Block) es un protocolo creado en 1985 por IBM (International Business Machines). Algunas veces es referido también como CIFS (Common Internet File System, [http://samba.org/cifs/](http://samba.org/cifs/)) tras ser renombrado por Microsoft en 1998. Entre otras cosas, Microsoft añadió al protocolo soporte para enlaces simbólicos y duros así como también soporte para ficheros de gran tamaño. Por mera coincidencia esto ocurrió por la misma época en que Sun Microsystems hizo el lanzamiento de WebNFS (una versión extendida de NFS, Network File System, [http://www.sun.com/software/webnfs/overview.xml](http://www.sun.com/software/webnfs/overview.xml)).

SMB fue originalmente diseñado para trabajar a través del protoclo NetBIOS (Network Basic Input/Output System), el cual a su vez trabaja sobre NetBEUI (NetBIOS Extended User Interface, o Interfaz de Usuario Extendida de NetBIOS), IPX/SPX (Internet Packet Exchange/Sequenced Packet Exchange, o Intercambio de paquetes interred/Intercambio de paquetes secuenciales) o NBT (NetBios over TCP), aunque también puede trabajar directamente sobre TCP/IP (Transfer Control Protocol/Internet Protocol, o Protocolo de Control de Transmisión/Protocolo de Internet)

1.2- Introducción acerca de Samba:

SAMBA ([http://www.samba.org/](http://www.samba.org/)) es un conjunto de programas, originalmente creados por Andrew Tridgell y actualmente mantenidos por The SAMBA Team ([http://www.samba.org/samba/team.html](http://www.samba.org/samba/team.html)), bajo la Licencia Pública General GNU ([http://www.gnu.org/](http://www.gnu.org/)), y que implementan en sistemas basados sobre UNIX el protocolo SMB. Sirve como reemplazo total para Windows NT, Warp, NFS o servidores Netware.

Este protocolo permite compartir varios recursos diferentes:
El acceso a las impresoras conectadas físicamente a las máquinas.
El acceso a los directorios compartidos.

El paquete SAMBA incluye utilidades para controlar el acceso de los archivos con la misma soltura que un WindowsNT.
Veremos más adelante como configurarlo en detalle, pero es posible:

    * Proteger por contraseña el acceso a un directorio compartido.
    * Proteger con una contraseña personificada para cada usuario, y dotar de permisos de acceso individualizados.

1.3- Composición del paquete SAMBA:

Dos o tres demonios se encargan de ofrecer los servicios del conjunto de aplicaciones de Samba. El primero es el smbd,
el segundo de ellos es el nmbd, y el tercero es el winbindd.

SMBD es el demonio que se encarga de los recursos compartidos: ficheros, impresoras, etc, pero también del control del acceso a los recursos. Gestiona los permisos de los diferentes clientes una vez que estos han sido identificados.

NMBD se ocupa de anunciar servicios. Es decir, se encarga de informar a las máquinas presentes en la red sobre cuales son los recursos disponibles. Este demonio maneja también la resolución de nombres de NetBIOS (Network Basic Input/Output System). Puede para ello comunicarse con un servidor WINS (Windows Internet Naming Service) presente en la red.

WINBINDD es un demonio que se inicia cuando Samba es miembro de un dominio Windows NT4 o ADS o cuando tiene relaciones de confianza con otro dominio. Éste demonio se referirá al archivo smb.conf para buscar la presencia de los parametros IdMap (Identity Mapping) UID (User Identifier) y GID (Group Identifier). Si son encontrados, winbindd utilizará los valores especificados para la asignación UID y GID. Si estos parámetros no existen, winbindd se inciará pero no será capaz de asignar ningún UID ni GID.

Nota: La resolución de nombres consiste en obtener una equivalencia entre la dirección IP de cada computadora y el nombre de la máquina.

1.4- El archivo smb.conf:

Samba utiliza un único archivo de configuración, llamado smb.conf, sito en /etc/samba/ que posee todas las entradas de configuración en modo texto, al estilo de los viejos archivos .ini de Windows.
Para explicar este archivo, nada mejor que trabajar sobre un ejemplo. A continuación, expongo un archivo de configuración muy muy básico, que como verán es bastante autocomprensible:

[global]
workgroup = migrupo
security = share
[ejemplo]
path = /home/publico
read only = no
guest ok = yes


Las palabras puestas entre corchetes ("[" y "]") significan lo que se llama una llave. Una llave sirve para establecer diferentes cosas. En este caso, utilizaremos 2 llaves, la "global" y la "compartido". La llave global establece directivas sobre cómo debe comportarse samba. En este caso, le especificamos a samba como se llama el grupo de trabajo.
La otra llave (compartido) es una llave donde cada uno puede establecer su nombre como le parezca, es decir, cada llave que se encuentre abajo de global será el nombre de como verán los otros usuarios de la red un recurso compartido.
En este caso cuando alguien se conecte a nuestra PC verá un recurso compartido llamado "compartido", y no necesariamente se tiene que llamar igual que la carpeta ("publico").

Ahora revisemos un poco para qué sirve cada clave:

NOTA: Algunas no aparecen en este ejemplo, pero en archivos de configuración más avanzados es altamente probable que las encuentren.

"workgroup": Esta clave define en que grupo de trabajo vamos a encontrarnos con los otros PC's de la red. 
Todos los PC's de la red deben tener el mismo nombre de grupo de trabajo, de lo contrario, no podrán compartir los recursos de red.

"security": Esta clave nos permite elegir entre compartir carpetas sin contraseña, o sea, a nivel servicio, o a nivel usuario, mediante la utilización de un usuario y una contraseña.

"path": Esta clave se utiliza para indicarle a samba la ruta de la carpeta que queremos compartir, independientemente del nombre que elijamos para compartirla. Recordar que para compartir una carpeta, primero debemos asegurarnos de poseer los permisos necesarios para efectuar las operaciones que consideremos oportunas. Si en una carpeta tenemos acceso de sólo lectura, y compartimos la carpeta para que los otros usuarios de la red puedan cambiar el contenido, no podrán debido a que la carpeta no tiene los permisos requeridos.

"read only": Como su nombre lo indica, esta clave establece si la carpeta compartida debe ser de solo lectura o no. Los valores posibles son "no" y "yes".

"guest ok": Esta clave es para habilitar lo que se llama el invitado, es para acceder sin usuario a una carpeta, y podamos verla. También supone un riesgo de seguridad esta clave, pero como estamos en un red hogareña, por el momento no nos interesa.

"netbios name": Esta clave nos permite establecer el nombre de nuestra computadora en la red.

"comment": Con esta clave, podremos agregarle un comentario a cada carpeta compartida.

"read list": Es la lista de usuarios que tienen acceso de sólo lectura a este servicio. Los usuarios de esta lista NO poseerán el acceso de escritura, por que la opción de sólo lectura está activada.

"valid users": Es la lista de usuarios que están permitidos para iniciar sesión en este servicio.

"write list": Es la lista de usuarios que tienen acceso de escritura y lectura a este servicio. Los usuarios de esta lista SI poseerán el acceso de lectura, por lo tanto no es necesario ponerlo junto con "read list". Aquí se utilizan juntos con fines de aprendisaje.

"encrypt passwords": Con esta clave le indicaremos a samba si queremos encriptar las contraseñas almacenadas en el sistema.

De esta forma, si yo cambio el archivo smb.conf de la siguiente manera:

[global]
workgroup = migrupo
security = share
[ejemplo]
path = /home/publico
read only = no
guest ok = yes

los otros usuarios de la red verán un recurso compartido llamado "ejemplo".

Si quiero compartir más de una carpeta, en este ejemplo llamada "datos", puedo hacer lo siguiente:

[global]
workgroup = migrupo
security = share
[publico]
path = /home/publico
read only = no
guest ok = yes
[segunda]
path = /media/datos
read only = yes
guest ok = yes

y los nombres de los recursos compartidos serán "publico" y "segunda".

Para modificar el nombre con el que aparecemos en la red, podemos agregar la siguiente línea en la llave global:

netbios name = <nombre>

Donde <nombre> puede ser cualquiera que nos guste, recordar hacer testparm para evitar problemas por posibles restricciones en los nombres netBIOS.

Para cambiar la descripción de una carpeta, debajo de cada llave con el nombre de la carpeta podemos agregar:

comment = Los archivos del emule


Así, un smb.conf de ejemplo nos podria quedar:

[global]
workgroup = migrupo
netbios name = pc_ricardo
security = share
[compartido]
path = /home/publico
read only = no
guest ok = yes
[emule]
path = /home/ricardo/descargas
comment = Los archivos del emule
read only = yes
guest ok = yes
[mp3]
path = /home/ricardo/mp3
comment = Musica
read only = yes
guest ok = yes

1.5- testparm, la utilidad de corrección de errores de samba:
Para probar la configuración, existe un programa llamado TESTPARM que lee el archivo de configuración y reporta cualquier error de sintaxis. Cualquier parámetro de configuración aún no establecido será ajustado a su valor por defecto. Recuerde que su archivo de configuración puede estar sintácticamente correcto pero no apropiado para su uso, por ejemplo, si no creamos la carpeta "publico" en /home/ testparm EN NINGÚN CASO devolverá código de error.

Para estar seguros de que todo ande bien, adjunto la salida de testparm en mi computadora. Si no es idéntica la salida, no importa, cambia dependiendo de cada configuración.

$testparm

Load smb config files from /etc/samba/smb.conf
Processing section "[compartido]"
Loaded services file OK.
Server role: ROLE_STANDALONE
Press enter to see a dump of your service definitions

[global]
        workgroup = migrupo
        security = share
[compartido]
        path = /home/publico
        read only = no
        guest ok = yes

Ahora bien, MODIFIQUÉ A PROPÓSITO el archivo smb.conf para que vean como testparm nos devela a donde se encuentra el error. 
Le sustraje la última letra a la primera clave, "workgroup" fue reemplazado por "workgrou" y ésta es la salida generada por testparm:

$testparm

Load smb config files from /etc/samba/smb.conf
Unknown parameter encountered: "workgrou"
Ignoring unknown parameter "workgrou"
Processing section "[compartido]"
Loaded services file OK.
Server role: ROLE_STANDALONE
Press enter to see a dump of your service definitions

[global]
        security = share
[compartido]
        path = /home/publico
        read only = no
        guest ok = yes

Fíjense cómo testparm nos avisa del error y automáticamente elimina la clave errónea, y, si levantáramos el servicio con este archivo de configuración, ignoraría las palabras clave sintácticamente incorrectas, provocando esto el mal funcionamiento, debido a que no estamos presentes en ningún grupo de trabajo. 

Hasta aquí hemos repasado un poco de teoría, ahora vayamos a la práctica.

2- como compartir carpetas sin contraseña:
Instalación de los paquetes correspondientes:
Debemos instalar desde los repositorios los siguientes paquetes para asegurarnos de poseer todas las herramientas necesarias para compartir archivos e impresoras de manera correcta:

sudo apt-get install samba samba-common samba-doc-pdf gsambad

Los paquetes samba y samba-common son los básicos de samba, samba-doc-pdf como su nombre lo indica es la documentación del mismo en formato PDF (Portable Data Format) y gsambad es una utilidad de configuración gráfica de samba.

Una vez terminado el proceso (exitoso) de instalación, procedemos a configurar samba para poder comenzar a compartir.

Lo primero que tenemos que hacer, es generar una copia de back-up del archivo de configuración de samba. Luego, independientemente de qué sistemas operativos tengamos en las computadoras, establecer un grupo de trabajo (el mismo en todas) y un nombre para cada computadora (distinto en todas).

Para lograr lo primero hacemos:

sudo cp /etc/samba/smb.conf /etc/samba/smb_old_0.conf

NOTA: El número se debe a que probablemente debamos configurar en reiteradas oportunidades este archivo, por lo tanto debemos generar distintos back-up's del mismo por razones de seguridad, de esta manera sabremos que el 0 (cero) es el predeterminado de instalación.

Para establecer el grupo de trabajo simplemente consta en ponerse de acuerdo sobre el nombre del mismo y poner el mismo en todas las computadoras, tengan el sistema operativo que tengan.

Ahora vamos a compartir una carpeta de ejemplo, la crearemos por una cuestión de comodidad en /home/

sudo mkdir /home/publico

Una vez creada la carpeta, debemos asignar los permisos necesarios para que los otros usuarios puedan acceder:

* Si queremos que los usuarios puedan escribir sobre la carpeta compartida ponemos:

sudo chmod 755 /home/publico

* Si queremos que SOLO PUEDAN LEER (no podrán escribir ni modificar ni borrar archivos) ponemos:

sudo chmod 555 /home/publico


Ahora bien, hecho esto pasamos a configurar directamente el archivo smb.conf. Por ahora, vamos a borrar completamente el contenido del archivo y vamos a copiar y a pegar exactamente esto:

para editar el archivo desde la interfaz gráfica: sudo gedit /etc/samba/smb.conf

para editar el archivo desde la consola (terminal): sudo nano /etc/samba/smb.conf

[global]
workgroup = migrupo
security = share
[compartido]
path = /home/publico
read only = no
guest ok = yes

Guardamos el archivo y ahora hay que comprobar si el archivo de configuración es correcto, para esto escribimos "testparm" en la terminal. (Ver apartado 1.5- Testparm, la utilidad de detección de errores de samba.)
Si todo salió bien, ahora debemos reiniciar el servidor samba para que tome los cambios propuestos, para esto hacemos:

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

 
3- Cómo compartir carpetas con usuario y contraseña:
Supongamos ahora que tenemos en una casa, 3 computadoras, y 3 usuarios, pero queremos que cada usuario acceda a una carpeta distinta, entonces debemos efectuar los siguientes cambios:

Antes que nada, debemos crear los usuarios los cuales tendrán acceso al recurso compartido. Para esto hacemos:

sudo useradd -s /sbin/nologin <nombre>

Donde <nombre> va el nombre de usuario que utilizaremos para que el otro usuario pueda ingresar.

Ejemplo: sudo useradd -s /sbin/nologin juan
         sudo useradd -s /sbin/nologin martin

Una vez creados el/los usuario/s debemos asignarles una contraseña, y para esto hacemos:

sudo smbpasswd -a <nombre>

Donde <nombre> va el nombre de usuario que utilizamos para los usuarios que creamos antes.

Ejemplo: sudo smbpasswd -a juan
         sudo smbpasswd -a martin

Cuando ejecutemos estas líneas en la consola nos pedirá que ingresemos la contraseña, y luego la misma otra vez, así no cometemos errores de tipeo. Yo a propósito cometí un error con el segundo usuario para que vean la salida del programa.

$ sudo smbpasswd -a juan

New SMB password:
Retype new SMB password:
Added user juan.

$ sudo smbpasswd -a martin

New SMB password:
Retype new SMB password:
Mismatch - password unchanged.
Unable to get new password.

$ sudo smbpasswd -a martin

New SMB password:
Retype new SMB password:
Added user martin.


Ahora debemos crear otra carpeta para compartirle al otro usuario, asignarle permisos de lectura y escritura a las dos carpetas, para poder manejar los permisos a nivel usuario (hasta ahora lo veníamos haciendo en modo servicio):

sudo mkdir /home/prueba

sudo chmod 755 /home/publico

sudo chmod 755 /home/prueba

Una vez generados los usuarios y creadas las carpetas con los permisos, vamos a modificar el smb.conf, para esto hacemos:

sudo cp /etc/samba/smb.conf /etc/samba/smb_old_1.conf

Para editar el archivo desde la interfaz gráfica: sudo gedit /etc/samba/smb.conf

Para editar el archivo desde la consola (terminal): sudo nano /etc/samba/smb.conf

[global]
workgroup = migrupo
netbios name = pc_ricardo
security = user
encrypt passwords = yes
[compartido]
path = /home/publico
comment = Carpeta de prueba de juan
valid users = juan
write list = juan
read list = juan
[tests]
path = /home/prueba
comment = Carpeta de prueba de martin
valid users = martin
write list = martin
read list = martin


Algo así nos quedaría para que ninguno tenga acceso a la otra carpeta que no deba. Guardamos y para que samba tome los cambios y testeamos que todo haya salido bien utilizando testparm:

$testparm

Load smb config files from /etc/samba/smb.conf
Processing section "[compartido]"
Processing section "[tests]"
Loaded services file OK.
Server role: ROLE_STANDALONE
Press enter to see a dump of your service definitions

[global]
        workgroup = migrupo
        netbios name = pc_ricardo

[compartido]
        comment = Carpeta de prueba de juan
        path = /home/publico
        valid users = juan
        read list = juan
        write list = juan

[tests]
        comment = Carpeta de prueba de martin
        path = /home/prueba
        valid users = martin
        read list = martin
        write list = martin


Ahora debemos reiniciar para que samba tome los cambios correctamente:

sudo /etc/init.d/samba restart

Muy bien, ahora el usuario "juan" sólo tiene acceso a la carpeta "compartido" y el usuario "martin" sólo tiene acceso a la carpeta "tests".

Ahora imaginemos que necesitamos que un tercer usuario ingrese a la carpeta de juan en modo SOLO LECTURA, NO a la de martin y que tenga acceso de lectura/escritura a su propia carpeta. Para esto hacemos:

sudo mkdir /home/jorge

sudo chmod 755 /home/jorge

sudo useradd -s /sbin/nologin jorge

sudo smbpasswd -a jorge

sudo cp /etc/samba/smb.conf /etc/samba/smb_old_2.conf

sudo nano /etc/samba/smb.conf

y modificamos el archivo de la siguiente manera:

[global]
workgroup = migrupo
netbios name = pc_ricardo
security = user
encrypt passwords = yes
[compartido]
path = /home/publico
comment = Carpeta de prueba de juan
valid users = juan, jorge
write list = juan
read list = juan, jorge
[tests]
path = /home/prueba
comment = Carpeta de prueba de martin
valid users = martin
write list = martin
read list = martin
[carpeta_tres]
path = /home/jorge
comment = Carpeta de prueba de jorge
valid users = jorge
write list = jorge
read list = jorge

Guardamos el archivo y seguimos:

testparm

sudo /etc/init.d/samba restart

Aquí podemos ver cómo con unas leves modificaciones ya habilitamos una nueva carpeta compartida y dimos acceso a un usuario a una carpeta que ya existía, sin modificar a los otros usuarios. 
Es importante prestar atención en que los usuarios van separados con COMAS en las listas de validación, lectura y escritura.


Esperamos que hayan sido exitosos con este COMO.
4- PREGUNTAS FRECUENTES:
4.1- ¿Cómo hago para detener el servicio samba?

sudo /etc/init.d/samba <orden>

Donde <orden> puede ser:

start: inicia el servicio
stop: detiene el servicio
restart: reinicia el servicio (Si el servicio no estaba iniciado, lo inicia)

ejemplo: sudo /etc/init.d/samba stop

         y la salida será:

         * Stopping Samba daemons...                                     [ OK ]

4.2) ¿Cómo hago para eliminar usuarios que creé?

        Para quitar la contraseña del servidor samba:

                sudo smbpasswd -x <nombre>

        Para quitar el usuario del sistema:

                sudo userdel <nombre>

4.3) ¡Mi Windows no me permite explorar el grupo de trabajo y estoy seguro de que hice correctamente este COMO!

        La respuesta es que muy posiblemente tengas un firewall activado. Acá adjunto la lista de puertos que usa samba para interactuar con el resto de la red. Debes asegurarte de que estos puertos estén abiertos para poder conectarte a tus recursos desde una PC con GNU/Linux.

Puerto 135/TCP - usado por el servicio smbd
Puerto 137/UDP - usado por el servicio nmbd
Puerto 138/UDP - usado por el servicio nmbd
Puerto 139/TCP - usado por el servicio smbd
Puerto 445/TCP - usado por el servicio smbd

        Si no tienes un firewall activado, capaz tampoco tengas el servicio de compartir recursos de red. Así que puedes probar con compartir una carpeta cualquiera desde tu Windows para asegurarte de que tienes todo habilitado, y luego habilitar la escritura, así descartas problemas.

---

### Post by YOGUI on 2008-02-18
Muchas gracias *faktorqm*! Me fue muy útil. 
Me queda una pregunta: Puedo hacer esto para compartir una carpeta que se encuentra en una partición Windows (NTFS)?
Es que no puedo desligarme del todo de la peste Win y tengo varios exe que compartir con otros usuarios. 

PD: La carpeta que quiero compartir es /Documents and Settings/Usuario/Mis Documentos/Carpeta Compartida/

Saludos

---

### Post by faktorqm on 2008-02-18
Hola lo probe con una carpeta cualquiera, y no hay problema, en mi caso lo probe con 

```

[pruebayogui]
path = /media/sistemaxp/Documents and Settings/Administrador/Configuración local/Datos de programa/Adobe
browseable = yes
writable = yes
guest ok = yes

```

Ahora bien, cuando me fui a otra pc a ver si andaba, andaba, pero no tenia permisos para ver el sistema. Eso lo tenes que ver vos cuando lo montas (yo lo monto como solo lectura para usuarios y rw para root, asi me aseguro de no borrar nada ;)). Si no tenes que darle permisos a la carpeta que vas a compartir y no hay drama.  (y a los archivos)
eso lo podes llegar a hacer con el siguiente comando: 

```
sudo chmod 755 -R /ruta/que/queres/compartir
```

Trata de no poner 777 como ves en muchos lugares por internet, eso es permisos totales para cualquiera y supone un riesgo de seguridad... Salu2!

---

### Post by YOGUI on 2008-02-18
> sudo chmod 755 -R /ruta/que/queres/compartir
El problema es que cuando pongo esa ruta me dice que media/sistemaxp/Documents no existe, que no se puede acceder a and, que settings/Administrador/Configuración no existe, etc. O sea: que hago con los espacios? Como pongo la ruta esa en  este comando?

---

### Post by niko_3100 on 2008-02-18
no es sistema xp es media/sda1/blablabla   sda1 es la particion donde tenes montado tu windows, puede ser sda1 o sda2 o sdaX fijate a ver si asi va.

---

### Post by faktorqm on 2008-02-18
Esta bien, el error ese es muy facil de "saltear", mientras vas escribiendo la ruta (solo funciona si esta bien escrita en un principio) apretas la tecla TAB y te va completando los directorios. Cuando hagas eso, vas a ver que antes de cada espacio te pone el caracter "\". Ese caracter se llama caracter de escape y sirve para "escapear" los espacios, las comillas, los apostrofes, y otros caracteres mas que no estan habilitados digamos en lo que es nombres para carpetas. Supongo yo que existen normas claras sobre eso. Como windows si admite ese tipo de caracteres por ser otro el sistema de archivos que usa, se compatibiliza con los caracteres de escape. 
De todas maneras, en el smb.conf va sin eso, yo lo puse directo como te mostre, pero para los permisos si o si necesitas ponerlo. Espero que te haya servido, contame como te fue. salu2!

---

### Post by YOGUI on 2008-02-18
Si, lo de sdaX ya sabía como era, el tema es con los espacios en blanco.
La carpeta que quiero compartir es "/media/sda1/Documents and Settings/Usuario/Mis Documentos/GuiDocs". El terminal cuando inserto el comando chmod con la ruta esta me interpreta hasta el primer espacio. O sea: me dice que no existe la carpeta "/media/sda1/Documents" y que el comando "and" no es valido, etc.. O sea que los espacios cortan la sentencia. En el cmd de win, esto se soluciona poniendo el archivo o carpeta entre comillas simples, es decir que quedaría así: /media/sda1/'Documents and Settings'/Usuario/'Mis Documentos'/GuiDocs
Lo que yo quería saber es como hago en Linux? 
Se entiende? No se si me expreso con corrección...
Gracias por la ayuda.

---

### Post by YOGUI on 2008-02-18
> **faktorqm said:**
> Esta bien, el error ese es muy facil de "saltear", mientras vas escribiendo la ruta (solo funciona si esta bien escrita en un principio) apretas la tecla TAB y te va completando los directorios. Cuando hagas eso, vas a ver que antes de cada espacio te pone el caracter "\". Ese caracter se llama caracter de escape y sirve para "escapear" los espacios, las comillas, los apostrofes, y otros caracteres mas que no estan habilitados digamos en lo que es nombres para carpetas. Supongo yo que existen normas claras sobre eso. Como windows si admite ese tipo de caracteres por ser otro el sistema de archivos que usa, se compatibiliza con los caracteres de escape. 
De todas maneras, en el smb.conf va sin eso, yo lo puse directo como te mostre, pero para los permisos si o si necesitas ponerlo. Espero que te haya servido, contame como te fue. salu2!

Eso es! Muchas gracias *faktorqm*! Un maestro...:)

---

### Post by YOGUI on 2008-02-18
Bueno, sigo con problemas. Desde otra Pc con Win veo la carpeta que quiero compartir pero cuando la quiero abrir me da que no tengo acceso.

Este es mi smb.conf
> [global]
workgroup = Vc
security = share
[compartido]
path = /home/publica
read only = no
guest ok = yes
[app]
path = /media/sda1/Documents and Settings/Sim/Mis Documentos/GuiDocs/App
browseable = yes
writable = yes
guest ok = yes

ya ejecuté esto:
> sudo chmod 755 -R /media/sda1/Documents\ and\ Settings/Sim/Mis\ Documentos/GuiDocs/App

A la carpeta "compartido" tengo acceso pero no tengo permiso de escritura y en "app" no tengo acceso. Qué estoy haciendo mal?:confused:

---

### Post by faktorqm on 2008-02-18
pregunta: tenes abiertos en el firewall los puertos 137, 138 y 139? En la seccion faq de mi tuto te avisa que si no los tenes no podes verlo. Si no sabes como abrir esos puertos, "sudo apt-get install firestarter" y es un GUI del iptables.
Hace "cat /etc/fstab" y "cat /etc/mtab". Si es una particion ntfs, la estas montando con ntfs-3g o con el controlador de ubuntu por defecto? salu2!

---

### Post by YOGUI on 2008-02-19
Me estoy mareando un poco. 
El firewall creo que no estaba instalado. instalé firestarter y no tengo idea como configurarlo... soy novato en linux, se nota?
> Hace "cat /etc/fstab" y "cat /etc/mtab". Si es una particion ntfs, la estas montando con ntfs-3g o con el controlador de ubuntu por defecto?
No entiendo para que sirve "cat". La partición ntfs la monté cuando instalé el sistema operativo.

---

### Post by faktorqm on 2008-02-19
Bien, cada vez que no sepas para que sirve algo, escribi "--help" al final de un comando.
Cat sirve para mostrar un archivo en la terminal. vendria a ser como el type de D.o.s. te acordas?
si no sabes como se usa, mejor borralo por que te mareas peor y te empieza a no andar nada. "sudo apt-get remove firestarter --purge"
Ahora bien, la herramienta ntfs-3g te permite escribir y leer casi perfectamente, como si estuvieras en windows. en como un mount pero para ntfs. 
"sudo apt-get install ntfs-3g" y por ejemplo, cuando arrancas, pones "ntfs-3g /dev/algo /media/puntodemontaje" entonces el tipo te lo monta ahi.
Ahora bien, si no te interesa escribir en la particion ntfs grandes cantidades de datos, y/o los otros no se te quejan por que tarda mucho o mas que antes, NO lo instales. siempre es mejor instalar la menor cantidad de cosas posibles para no sobrecargar el sistema con 15 cosas de las cuales sirven 4 y usas 2.
Para verificar fehacientemente que tenes los puertos abiertos te podes instalar un scanner de puertos, el famoso nmap. "sudo apt-get install nmap nmapfe" el nmapfe es la interfaz grafica, entonces te escaneas a vos mismo y te dice ahi que puertos tenes abiertos. De paso te podes escanear algun server del laburo ;) jajaja salu2!

---

### Post by YOGUI on 2008-02-19
El 139 y el 445 están abiertos, pero no veo el 137 y el 138. Como hago para abrirlos?

Esto dice el nmapfe
> 111/tcp  open  rpcbind
139/tcp  open  netbios-ssn
445/tcp  open  microsoft-ds
631/tcp  open  ipp
1723/tcp open  pptp
2049/tcp open  nfs

---

