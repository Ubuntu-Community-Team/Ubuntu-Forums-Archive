---
title: "Edubuntu Classroom server"
date: 2007-04-24
forum: Argentina Team
---

### Post by electronpositivo on 2007-04-24
Hola!

Acabo de instalar Edubuntu ClassRoom Server 7.04 en un ordenador como servidor y en otro como estación de trabajo (así lo pone en el menú de instalación), pero no veo ninguna diferencia entre ambos.

Pensé que al iniciarlos aparecería como un tutorial con pasos a seguir, pero nada de nada. He visto que lleva el "Thin client manager", pero al abrirlo no aparece ningún equipo ni veo forma de agregarlo.

Agradecería me echárais un cable con lo que quiero hacer (si es posible, claro): mi sueño es poder crear varios usuarios en el servidor y que estos puedan acceder desde cualquier cliente y tener una unidad personal (alojada en el servidor).

Cuando leí aquello de "ClassRoom Server" pensé que sería posible hacerlo de una forma más fácil, pero por ahora no sé por donde seguir.

Gracias por vuestras respuestas!

---

### Post by marianom on 2007-04-24
Estuve buscando un poco y realmente hay poca información so far.
Mi recomendación: conectate con el LoCo chileno ya que ellos, actualmente, están mucho más orientados a edubuntu. [Aca]("https://wiki.ubuntu.com/EdubuntuChile") hay información de contacto para que los encuentres por irc.

---

### Post by gepatino on 2007-04-24
No conozco el edubuntu classroom server, pero use bastante ubuntu con ltsp, y segun tengo entendido, edubuntu se basa en ltsp para hacer lo que (segun entendi) necesitas.

En teoria en las maquinas clientes no tenes que instalar nada (de ahi el termino clientes delgados o thin clients), y en el servidor tenes que instalar dhcp + tftp + nfs + un chroot con el filesystem de los clientes.

Una vez que tenes todo configurado, solo te queda reiniciar los clientes indicandoles que booteen desde la red y listo, vas a ver que despues de bootear te ofrecen un login grafico directamente al servidor. A partir de ese momento, todas las aplicaciones funcionan del lado del servidor, y nada queda en el cliente (solo el servidor x, para pintar la pantalla y controlar mouse+teclado)

Este proyecto nacio bastante antes de edubuntu, pero ultimamente se mejoro mucho, se llama LTSP, y me parece que lo deberías tener instalado (por eso de edubuntu classroom server)

---

### Post by lugonesjoaquin on 2007-04-25
¿Lo que tratas de hacer no se puede solucionar instalando un servidor FTP?

Si es eso, no parece tan dificil, yo solo traté una vez de la forma más facil que hay (Pero de las peores, si quieres instalar un servidor profesional) y es instalando *ftpd*

Luego editas el archivo /etc/ftpusers para agregar los usuarios que no se podran loguear en el servidor, como root o anonymus. Luego desde cualquier cliente FTP escibes la IP del equipo, el usuario (Que se yo, pedro, imageinate) y la contraseña y listo, se logueará en el home de pedro.

Obviamente esta NO es una de las mejores maneras de hacerlo, al contrario, hay muchisimas mejores, pero es de la unica que te puedo contar la experiencia.

Googlea un poco, hay mucha informacion al respecto, no neceitas una distro especial ni nada.

Suerte!

Edito: Aqui hay un manual sobre como instalar un servidor ftp con usuarios virtuales y todas esas cositas:
[http://tuquito.org.ar/tukipedia/index.php?title=Servidor_ftp_con_usuarios_virtuales](http://tuquito.org.ar/tukipedia/index.php?title=Servidor_ftp_con_usuarios_virtuales)

---

### Post by clasificado on 2007-04-25
[quote=edubuntu.com]Installing from the CD will provide you with an out of the box working thin client environment, including sound and thin client block device support.[/quote]

Por lo que entiendo de acá, todo lo necesario para que el LTSP funcione ya estaria instalado.

No lo probé pero me parece que te instalas el servidor edubuntu y ya está. Es solo cuestion de hacer que las pcs boteen desde red configurando el bios (sin nada instalado, no hace falta).

Clasificado

---

### Post by electronpositivo on 2007-05-30
A ver si lo entendí, entonces se trata de utilizar clientes ligeros, no?

Yo pensé que me ayudaría a realizar mi sueño... poder crear varios usuarios en el servidor y que estos puedan acceder desde cualquier cliente y tener un directorio personal (alojado en el servidor).

¿Sabéis si esto es posible? ¿Algun howto interesante?

Por cierto, muy original la idea de hacerlo por ftp, jeje, revisaré el manual, gracias.

---

### Post by elrengo79 on 2007-05-30
yo instale un edubuntu server y ya viene con todo lo que necesita el ltsp, lo unico que tenes que hacer es fijarte que el archivo de configuracion del servidor dhcp tenga los valores de tu red  (/etc/ltsp/dhcpd.conf)
Despues de eso entra a la bios de la pc cliente y seteala para que inicie desde la red

PD: el sistema que tiene que soportar el cliente se llama PXE, en mi caso la pc utilizaba otro sistema y no tenia comunicacion, una solucion a eso es generar un diskette con una rom de booteo para el modelo de tu placa.
La podes bajar desde [http://rom-o-matic.net](http://rom-o-matic.net)

si te surge algun problema, en [https://help.ubuntu.com/community](https://help.ubuntu.com/community) tenes mucha info sobre ltsp

PD2: Para instalar ltsp desde cualquier otro ubuntu es muy simple tambien
sudo apt-get install ltsp-server-standalone openssh-server
sudo ltsp-build-client #tarda un buen rato hasta que baja y genera todo el sistema
y luego modificar el .conf del dhcp server

---

### Post by electronpositivo on 2007-06-01
Muchas gracias por vuestra ayuda. He aprendido cosas muy interesantes... pero no sé si me conviene hacerlo de esa forma.

He entendido que LTSP se utiliza para utilizar equipos algo escasos de recursos conectándolos a un servidor que debe ser bastante potente, pero este no es mi caso. Se trata de equipos medios todos (25 pcs), incluido el servidor, que es igual que el resto (Duron 2000 y 256 de ram), con lo cual me parece inadecuado que 24 pcs utilicen los recursos de uno de ellos para ejecutar los programas.

Ahora, pregunta: ¿Se puede utilizar LTSP solamente para autenticar contra el servidor y almacenar los archivos en este, dejando la ejecución de programas del lado de cada cliente?

---

### Post by gepatino on 2007-06-01
> **electronpositivo said:**
> 
Ahora, pregunta: ¿Se puede utilizar LTSP solamente para autenticar contra el servidor y almacenar los archivos en este, dejando la ejecución de programas del lado de cada cliente?


Con LTSP podes configurar algunas aplicaciones para que corran del lado del cliente, pero lo más pesado, que sería el escritorio completo (gnome o kde) me parece que no se puede. Busca algo sobre LocalApps en LTSP.

Si esta opcion no cumple con lo que necesitas, podes configurar un LDAP en el server para que todos los clientes se logueen contra el, no es tan dificil como suena. A esto le podes agregar que los clientes monten los homes desde el server (via nfs) o que se sincronicen automaticamente mediante algun script prelogin/postlogin que haga un rsync o algo similar.

Saludos,

---

### Post by electronpositivo on 2007-11-15
> **gepatino said:**
> 
Si esta opcion no cumple con lo que necesitas, podes configurar un LDAP en el server para que todos los clientes se logueen contra el, no es tan dificil como suena. A esto le podes agregar que los clientes monten los homes desde el server (via nfs) o que se sincronicen automaticamente mediante algun script prelogin/postlogin que haga un rsync o algo similar.

Saludos,

Gracias! Eso es lo que he hecho finalmente:
[LIST]
[*]LDAP en el server
[*]homes en el server
[*]Conexión automática de homes en cada cliente mediante nfs (en el fstab)
[/LIST]

¿Es esta la mejor opción?

En esto todavía tengo un pequeño problemilla... y es que al arrancar cada cliente sucede bastantes veces que no se enlaza la unidad 'home local' con la 'home del server' y lo que hacemos es reiniciar cada cliente al que le pasa.

Este es el fstab de cada cliente:
[FONT="Courier New"]# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda2  /               ext3    defaults,errors=remount-ro 0       1
/dev/hda4  /boot           ext3    defaults        0       2
[COLOR="Green"]192.168.1.200:/home /home/	nfs	defaults	1	1
[/COLOR]
/dev/hda8  none            swap    sw              0       0
/dev/hdb        /media/cdrom0   udf,iso9660 user,umask=000,noauto,gid=46     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,umask=000  0       0[/FONT]

En verde la línea que hace posible la conexión.
¿Se os ocurre algo?

---

