---
title: "Login y autenticación con smart card o token"
date: 2016-08-08
forum: Argentina Team
---

### Post by eamestoy on 2016-08-08
**[SIZE=4]ACTUALIZACION, CUSTOMIZACIÓN Y TRADUCCIÓN AL ESPAÑOL BASADO EN EL HILO[/SIZE]: [https://ubuntuforums.org/showthread.php?t=1557180](https://ubuntuforums.org/showthread.php?t=1557180)**

(Testeado en Ubuntu 14.04 y Ubuntu 16.04)

El objeto de esta tarea es lograr no depender del intercambio en "papel" de contraseñas, fundamentalmente para realizar tareas administrativas en puestos de trabajo Linux.
Para ello se configuran herramientas que permiten la autenticación con certificados almacenados en tokens o smart cards.

***1.- Pre Requisitos***

Partimos de un PC con Ubuntu 16.04 instalado con una configuración básica. Se entiende que es 100% aplicable a cualquier distribución Linux basada en Debian.
Se utiliza paquetería .deb de los repositorios de la distribución y en los ejemplos se utiliza la herramienta apt para su instalación.

**NOTA 1**

Para todos los ejemplos se asume que se trabaja con un usuario con permisos de sudoer. Si el usuario lo desea puede realizar todas las tareas como root; en dicho caso deberá omitir el comando sudo así como comandos ejecutados con permiso de usuario standard. Si por el contrario no cuenta con permisos de sudoer deberá solicitarlo o crearlo con visudo o editando /etc/group para añadirlo al grupo sudo.

**NOTA 2**

Se asume que las tarjetas a ser utilizadas están inicializadas con estructura PKCS11 y ya poseen almacenados los certificados X.509 y llaves RSA correspondientes. Se omite el almacenamiento de llaves SSH para controlar accesos remotos con las tarjetas. Es interesante referir a la definición de standares PKCS para la normalización de procedimientos así como para la adquisición de hardware de criptografía.

En el capítulo 7  se detallan opciones nativas Linux para generación y almacenamiento de certificados y llaves así como crear las estructuras PKCS11 necesarias y otras funcionalidades útiles en la consola.

**NOTA 3**

Para la redacción de este tutorial se ha utilizado como base la información recogida en este link: [https://ubuntuforums.org/showthread.php?t=1557180](https://ubuntuforums.org/showthread.php?t=1557180) mas investigación, pruebas de ensayo y error y adaptación a las necesidades propias del estudio.

A la fecha el sitio oficial del proyecto OpenSC fue mudado de [http://www.opensc-project.org](http://www.opensc-project.org) a [https://github.com/OpenSC](https://github.com/OpenSC)

***2.-  Paquetes y dependencias***

Son necesarios los siguientes paquetes:
coolkey
pcscd (demonio)
pcsc-tool
pkg-config
libpam-pkcs11
opensc
libengine-pkcs11-openssl

Procedemos a instalar los paquetes:

```
$ sudo apt-get install coolkey pcscd pcsc-tools pkg-config libpam-pkcs11 opensc libengine-pkcs11-openssl
```

[http://amestoy.info/wp-content/uploads/2016/08/instalación-paquetes-pcsc-1.png](http://amestoy.info/wp-content/uploads/2016/08/instalación-paquetes-pcsc-1.png)

3.-  Archivos de configuración

Se sugiere cambiar la ruta por defecto del archivo de log de OpenSC así como el nivel de log, según el siguiente detalle:

```
$ sudo nano /etc/opensc/opensc.conf
```

app default {
# Amount of debug info to print
#
# A greater value means more debug info.
# Default: 0
#
# debug = 0;
debug = 5;
# The file to which debug output will be written
#
# Special values 'stdout' and 'stderr' are recognized.
# Default: stderr
#
# debug_file = /tmp/opensc-debug.log
debug_file = /var/log/opensc-debug.log

En el mismo archivo puede ser necesario (no lo fue para la instalación en Ubuntu 14.04 ni 16.04) buscar provider_library y quitar el &#8220; # &#8220; inicial para descomentar la línea.

# Default: libpcsclite.so.1
# provider_library = libpcsclite.so.1

El paquete libpam-pkcs11, encargado de manejar la autenticación con tokens o smart cards, no crea los archivos de configuración por defecto.

Por ello es necesario crearlos &#8220;a mano&#8221;:

```
$ sudo mkdir /etc/pam_pkcs11
$ zcat /usr/share/doc/libpam-pkcs11/examples/pam_pkcs11.conf.example.gz | sudo tee /etc/pam_pkcs11/pam_pkcs11.conf
```

Creamos también los directorios para almacenar los certificados de las CA&#8217;s en las que se hace confianza así como para las Certificate Revocation Lists enviadas por las correspondientes CA&#8217;s

```
$ sudo mkdir /etc/pam_pkcs11/cacerts /etc/pam_pkcs11/crls
```

Finalmente copiamos los certificados de las CA&#8217;s de confianza en el directorio cacerts. Luego realizamos el rehash de todos los certificados almadenados. En el ejemplo copiaremos el certificado del Servicio Central de Informática de la UdelaR - SeCIU:

```
$ cd /etc/pam_pkcs11/cacerts
$ sudo wget http://www.seciu.edu.uy/ca/CARAIZ2UDELAR.pem
$ sudo pkcs11_make_hash_link
```

[http://amestoy.info/wp-content/uploads/2016/08/salida-pkcs11_make_1.png](http://amestoy.info/wp-content/uploads/2016/08/salida-pkcs11_make_1.png)

***4.-  Almacenar certificados de usuario***

Para grabar el o los certificados almacenados en una tarjeta o token en la caché del usuario logueado ejecutamos el siguiente comando.
El directorio donde serán almacenados los certificados es: /home/{nombre-usuario}/.eid/cache/

```
$ pkcs15-tool -L
```

[IMG]http://amestoy.info/wp-content/uploads/2016/08/pkcs15-tool-salida-1.png[/CODE]

MUY IMPORTANTE: El CN (common name) que aparece en el certificado, &#8220;Enrique Amestoy&#8221; por ejemplo, debe ser el nombre del usuario linux, sin comas al final. En caso contrario debe modificarse en /etc/password. La línea del nombre de usuario quedaría:

usuarioXX1:x:1003:1003:{nombre-usuario}:/home/usuarioXX1:/bin/bash

***5.-  Autenticar acceso sudo***

Debemos editar el archivo /etc/pam.d/sudo e incluir auth sufficient pam_pkcs11.so. Debería verse como el siguiente código:

#%PAM-1.0

auth sufficient pam_pkcs11.so

@include common-auth
@include common-account

session required pam_permit.so
session required pam_limits.so

[http://amestoy.info/wp-content/uploads/2016/08/sudo-login-smart-card.png](http://amestoy.info/wp-content/uploads/2016/08/sudo-login-smart-card.png)

***6.-  Autenticación de login***

En este caso editamos el archivo /etc/pam.d/common-auth. Agregando el módulo pam_pkcs11.so de autenticación.
Al comienzo debe verse asi:

# To take advantage of this, it is recommended that you configure any
# local modules either before or after the default block, and use
# pam-auth-update to manage selection of other modules.  See
# pam-auth-update(8) for details.
# AÑADIMOS LA LINEA A CONTINUACIÓN
auth    [success=3 default=ignore]  pam_pkcs11.so

[http://amestoy.info/wp-content/uploads/2016/08/ubuntu-login-smart-card-2.jpg](http://amestoy.info/wp-content/uploads/2016/08/ubuntu-login-smart-card-2.jpg)

Realizado lo anterior estamos en condiciones de autenticar con token en primer lugar. En caso de que falle se pasa a la clásica autenticación por contraseña.

Es posible deshabilitar la contraseña del usuario para que solo autentique con token. Una opción para hacerlo es la siguiente:

```
$ sudo passwd -l `whoami`
```

***7.-  Comandos de consola útiles***

A) Visualizar la información contenida en un token

```
$ pkcs15-tool -D
```

[http://amestoy.info/wp-content/uploads/2016/08/salida_pkcs15-tool-D.png](http://amestoy.info/wp-content/uploads/2016/08/salida_pkcs15-tool-D.png)

B) Visualizar las lectoras conectadas a un equipo

```
$ opensc-tool --list-readers
```

# Detected readers (pcsc)
Nr.  Card  Features  Name
0     Yes             SCM Microsystems Inc. SCR 331 [CCID Interface] (21120544104490) 00 00

C) Identificar el nombre de la tarjeta/token insertado

```
$ opensc-tool --reader 0 --name
```
STARCOS SPK 2.3

D) Inicializar o formatear el filesystem de una tarjeta/token

```
$ pkcs15-init -C --label "Tarjeta Soporte 155"
```
Using reader with a card: SCM Microsystems Inc. SCR 331 [CCID Interface] (21120544104490) 00 00
New Security Officer PIN (Optional - press return for no PIN).
Please enter Security Officer PIN:

E) Inicializar o formatear el filesystem de una tarjeta/token

```
$ pkcs15-init -C --label "Tarjeta Soporte 155"
```
Using reader with a card: SCM Microsystems Inc. SCR 331 [CCID Interface] (21120544104490) 00 00
New Security Officer PIN (Optional - press return for no PIN).
Please enter Security Officer PIN:

F) Generar un par de claves (se usa 1024 ya que la tarjeta de testing no permite 2048 o 4096) y las almaceno en la tarjeta/token

```
$ pkcs15-init -G rsa/1024 --auth-id id-usuario --label "Mi clave Privada" --public-key-label "Mi clave Publica"
```
Using reader with a card: SCM Microsystems Inc. SCR 331 [CCID Interface] (21120544104490) 00 00
Security officer PIN unlock key required.
Please enter Security officer PIN unlock key:

G) Sustituímos &#8220;id-usuario&#8221; por el  aut-id que podemos tomarlo luego de ejecutar pkcs15-tool -D, en la sección PIN.

Podemos leer la parte pública de un certificado en la tarjetas

```
$ pkcs15-tool --read-public-key 556655
```
Using reader with a card: SCM Microsystems Inc. SCR 331 [CCID Interface] (21120544104490) 00 00
-----BEGIN PUBLIC KEY-----
MIGfMA0GCSqGSIb3DQEBAQUAA4GNADCBiQKBgQC4scyLp6Z1xiaAf0XOuRzQ2Bl6
vjYDYz7f3h7F5+xyZTvLlz+WobTb0ETmVQb1aBmQFq2l95VN7WLFbM+q0INoKsvj
SszwbffepmbHk4BRXHhHIZ56yhCCxb1oCBzh82C0BvgviWdyReINGaR+aEPfKyR5
4Oc34589eadx+o5uPQIDAQAB
-----END PUBLIC KEY-----

Debemos sustituir &#8220;556655&#8221; por el ID que nos devuelve pkcs15-tool -D

H) Almacenar en la tarjeta/token un certificado ya existente, creado con openssl

```
$ openssl genrsa -des3 -out mykey.key 1024
```

---

### Post by wildmanne39 on 2016-08-08
*Thread moved to **Argentina Team**.*

---

