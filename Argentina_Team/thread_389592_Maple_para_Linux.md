---
title: "Maple para Linux"
date: 2007-03-20
forum: Argentina Team
---

### Post by jotacebusta on 2007-03-20
Saludos,

Acabo de descargar una versión de Maple 10 para Linux con aMule, soy usuario de ubuntu 6.10, y estoy tratando de instalr al nuevo juguete... ya tengo el archivo maple.linux.v10.intaller.bin, pero no tengo idea de qué hacer con él. Si alguien me puede ayudar quedaré sumamente agradecido.

gracias de antemano

Jotace

---

### Post by marianom on 2007-03-20
Primero te aseguras que tenga permisos de ejecución:

```
chmod +x maple.linux.v10.intaller.bin
```

y luego lo ejecutas:

```
./maple.linux.v10.intaller.bin
```

Con eso debería funcionar.

---

### Post by DuckMan on 2007-03-20
pregunta n00b:

q es maple?

EDIT: borren esto, por un segundo me olvide de google

---

### Post by clasificado on 2007-03-22
Otra forma de hacer *exactamente lo mismo*, esta vez dentro de KDE || Kubuntu:

1) En las **propiedades** del archivo

[img]http://serv2.imagehigh.com/imgss/5426154_ejecutable.2.png[/img]

2) **Lo haces ejecutable**:
a: En linux, lo ejecutable no tiene que ver con la extension, sino con este tilde. 
b: Los bin se pueden ejecutar, como si fueran los exe en windows, pero no son los únicos.
c: De todo lo que se baja de internet, *nada se puede ejecutar* automaticamente. Lo tenes que autorizar dandole a este tilde.

[img]http://serv2.imagehigh.com/imgss/5426156_ejecutable.3.png[/img]

3) **Doble click** y ejecuta.

Clasificado

---

### Post by jotacebusta on 2007-03-22
Gracias por sus respuestas. Hice lo que me indicaron, pero no funcionó... a continuación copio el mensaje de error que obtuve..

Si entiendo bien las cosas tengo que bajar un par de librerías más, ¿cierto?

Luego de consultar a Google, fui a [http://rpmfind.net/linux/RPM/Distribs.html](http://rpmfind.net/linux/RPM/Distribs.html) y no hay la distribución Ubuntu 6.10 (ni ninguna UBUNTU de hecho... )

¿Algo especial para bajar las librerías?


Gracias de nuevo,


jotace


Preparing to install...
Extracting the JRE from the installer archive...
Unpacking the JRE...
Extracting the installation resources from the installer archive...
Configuring the installer for this system's environment...
nawk: error while loading shared libraries: libm.so.6: cannot open shared object                                 file: No such file or directory
dirname: error while loading shared libraries: libc.so.6: cannot open shared obj                                ect file: No such file or directory
/bin/ls: error while loading shared libraries: librt.so.1: cannot open shared ob                                ject file: No such file or directory
basename: error while loading shared libraries: libc.so.6: cannot open shared ob                                ject file: No such file or directory
dirname: error while loading shared libraries: libc.so.6: cannot open shared obj                                ect file: No such file or directory
basename: error while loading shared libraries: libc.so.6: cannot open shared ob                                ject file: No such file or directory
hostname: error while loading shared libraries: libc.so.6: cannot open shared ob                                ject file: No such file or directory

Launching installer...

grep: error while loading shared libraries: libc.so.6: cannot open shared object                                 file: No such file or directory
/tmp/install.dir.9814/Linux/resource/jre/bin/java: error while loading shared li                                braries: libpthread.so.0: cannot open shared object file: No such file or direct                                ory
jcelena@mocosita:~/Desktop/Maple_FILES/Setup$

---

### Post by strugart on 2007-03-22
Los rpm se trasforman en deb mediante alien. Que se baja con apt-get (si no lo tenes).
Osea bajate el alien si no lo tenes, converti el paquete y seguro que se te bajan las cosas. Si no revisa aca (si no te bajan los paquetes : 
[http://packages.ubuntu.com/](http://packages.ubuntu.com/). 
Espero haber ayudado. Strugart

---

### Post by jotacebusta on 2007-03-22
Gracias strugart, pero no ha funcionado.

hice sudo apt-get install lib..., y el sistema dice que no encuentra los paquetes:


:~$ sudo apt-get install libm.so.6
Password:
Leyendo lista de paquetes... Hecho
Creando árbol de dependencias
Leyendo información de estado... Hecho
E: No se pudo encontrar el paquete libm.so.6

:~$ sudo apt-get install librt.so.1
Leyendo lista de paquetes... Hecho
Creando árbol de dependencias
Leyendo información de estado... Hecho
E: No se pudo encontrar el paquete librt.so.1


En la página a la que me dirigiste no encuentro los paquetes tampoco...


gracias


jotace

---

### Post by clasificado on 2007-03-23
A veces para buscar paquetes es mas facil con una utilidad gráfica (Synaptic o Adept).

Por linea de comando las busquedas se hacen con 
```

sudo apt-cache search libc

```

De cualquier forma, probá instalando el paquete es **libc6**

Por otra parte: ¿Tenes instalado java? tengo la sensacion de que tu programa lo necesita

---

### Post by strugart on 2007-03-23
En los repositorios no están ninguno de tus paquetes. Digamos fíjate en synaptic si hay alguno parecido e instalalo (talvez si están en los repositorios pero con otro nombre o nombre parecido).
Otra cosa trataste de bajar el rpm y convertirlo con alien?

---

### Post by marianom on 2007-03-23
ese error también puede darse por no tener permisos de lectura.
En mi maquina ese file existe:
```
mariano@mishima:~$ slocate libc.so.6
/lib/tls/i686/cmov/libc.so.6
/lib/libc.so.6
/opt/oracle/product/10.2.0/client_1/lib/stubs/libc.so.6

```

Proba con

```
sudo ./maple.linux.v10.intaller.bin
```

a ver como te va.

---

### Post by jotacebusta on 2007-03-24
Hola de nuevo,


He hecho básicamente lo que me han sugerido, pero no funcionan las cosas. Más abajo los comandos que ejecuté y lo que obtuve...


Lo que si definitivamente no tengo idea de como hacer es "bajr los rpm y transformalos con el alien". Buequé en synaptic y no hay nada que se parezca a alien... Si me puedes dar instrucciones más detalladas al respecto... 

mil gracias


JC

- Instalé Java (que ya estaba, sólo agregué alguna cosa)
- Ejecuté sudo apt-cache search libc, y la cosa parece funcionar bien. 
- sudo apt-get install libc6
Leyendo lista de paquetes... Hecho
Creando árbol de dependencias
Leyendo información de estado... Hecho
libc6 ya está en su versión más reciente.
Los siguientes paquetes fueron instalados automáticamente y ya no son necesarios:
  libcvsservice0 libsp1c2 unicode-data sp tidy libtidy-0.99-0 cvs libxine-main1 kfilereplace linuxdoc-tools latex-xcolor
  quanta-data
Use «apt-get autoremove» para desinstalarlos.
0 actualizados, 0 se instalarán, 0 para eliminar y 0 no actualizados

- Ejecuté slocate libc.so.6
slocate libc.so.6
/lib/tls/i686/cmov/libc.so.6
/lib/libc.so.6

- Y luego sudo ./maple.linux.v10.intaller.bin
Preparing to install...
Extracting the JRE from the installer archive...
Unpacking the JRE...
Extracting the installation resources from the installer archive...
Configuring the installer for this system's environment...
nawk: error while loading shared libraries: libm.so.6: cannot open shared object file: No such file or directory
dirname: error while loading shared libraries: libc.so.6: cannot open shared object file: No such file or directory
/bin/ls: error while loading shared libraries: librt.so.1: cannot open shared object file: No such file or directory
basename: error while loading shared libraries: libc.so.6: cannot open shared object file: No such file or directory
dirname: error while loading shared libraries: libc.so.6: cannot open shared object file: No such file or directory
basename: error while loading shared libraries: libc.so.6: cannot open shared object file: No such file or directory
hostname: error while loading shared libraries: libc.so.6: cannot open shared object file: No such file or directory

Launching installer...

grep: error while loading shared libraries: libc.so.6: cannot open shared object file: No such file or directory
/tmp/install.dir.21584/Linux/resource/jre/bin/java: error while loading shared libraries: libpthread.so.0: cannot open shared object file: No such file or directory

---

### Post by marianom on 2007-03-24
Si la librería está y el sudo no funciona, falta setear alguna variable de entorno (e.g. LD_LIBRARY_PATH). Todos los productos de oracle vienen en bin y con java y me harté que me pasaran esos errores. Creo que el tema anda por ahí.
Si hago tiempo en estos días, investigo un poco a ver que descubro.

---

