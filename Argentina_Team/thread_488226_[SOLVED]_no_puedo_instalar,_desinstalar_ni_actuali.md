---
title: "[SOLVED] no puedo instalar, desinstalar ni actualizar"
date: 2007-06-29
forum: Argentina Team
---

### Post by Timbis on 2007-06-29
con cualquie programa o po medio de la terminal, me salta el error: " files list file for package `python-qt3' is missing final newline", quiero forzar la desinstalacion, pero me salta que tiene dependencias, por ende no se puede desinstalar.
alguien sabe como borrar y reinstalar el archivo?
gracias de antemano.

---

### Post by jpmorelli on 2007-06-29
Probá haciendo:

sudo apt-get -f install 

que resuelve las dependencias que quedaron sin resolver

o sino:

sudo dpkg --configure -a

que termina de configurar instalaciones que quedaron a medias ( creo ;) )

Suerte !

---

### Post by Timbis on 2007-06-29
nop, no cambio nada. gracias igual
lo ultimo que instale fue el amarok, que viene tambien con el paquete amarok-xine, yo creo que este es el paquete roto ya que no me funciona el programa. trate de forzarlo, pero me sige dando el mismo error.

---

### Post by odiseo77 on 2007-06-30
Hola, prueba lo siguiente a ver si da resultados (no estoy seguro del todo, pero con intentar no se pierde nada):

```
sudo apt-get update && sudo apt-get install --reinstall python-qt3
```

Saludos, ¡¡y suerte!!

---

### Post by Timbis on 2007-06-30
odiseo77, gracias por tu ayuda, Hubiera sido la solucion porque intento reinstalarlo, pero este dichoso python-qt3 no me permite instalar nada, les paso el error cuando intente reinstalarlo:

Antes de esto va lo que descarga.
Seleccionando el paquete python-qt3 previamente no seleccionado.
(Leyendo la base de datos ... dpkg: error al procesar /var/cache/apt/archives/python-qt3_3.17-0ubuntu3_i386.deb (--unpack):
[COLOR="Red"] files list file for package `python-qt3' is missing final newline[/COLOR]
Se encontraron errores al procesar:
 /var/cache/apt/archives/python-qt3_3.17-0ubuntu3_i386.deb
Proceso detenido por haber demasiados errores.
[COLOR="Red"]E: Sub-process /usr/bin/dpkg returned an error code[/COLOR] (1)
 
yo creo que la solucion es modificar alguna lista de paquetes instalados, pero no se cual.

---

### Post by odiseo77 on 2007-06-30
ok, buscando en google encontré [esto]("http://linuca.org/pipermail/linuxcantabria/2004-March/003901.html"), asi que, al parecer, la solución sería ejecutar:

```
sudo dpkg -i --force-overwrite /var/cache/apt/archives/python-qt3_3.17-0ubuntu3_i386.deb
```

Y luego:

```
sudo dpkg --configure -a
```

Saludos, y espero te funcione.

---

### Post by Mauro22 on 2007-06-30
Hola, 


a mi me paso algo parecido tratando de instalar el compiz fusion

lo que hice fue ejecutar Synaptic, fui a filtros -> rotos, y a los paquetes de la lista les di clic derecho -> eliminar completamente


y listo!, ya puede actualizar otra vez, es mas, acaba de salir una version de beryl. Beryl SVN. Trae un par de cosas mas.

saludos!

---

### Post by Timbis on 2007-06-30
Pegue esto en la terminal: sudo dpkg -i --force-overwrite /var/cache/apt/archives/python-qt3_3.17-0ubuntu3_i386.deb.
Y me da el mismo error de antes.

Con respecto a los paquetes rotos, en sinaptic no aparece nada en la lista.

He revisado los foros de ubuntu-ar/-es en ingles y en castellano, y e visto muchos problemas iguales, muchos parecieran no tener solucion.

No importa que me lleve años arreglar este problema, seguire utilizando Linux.

---

### Post by Al_maverick on 2007-06-30
puedes hacer un update?
si es asi, proba lo siguiente:
comenta todos los repositorios en /etc/apt/spurces.list
sudo apt-get update
sudo apt-get clean
sudo apt-get -f install
descomenta los repositorios
sudo apt-get update

---

### Post by Timbis on 2007-07-01
Si, el update lo hace perfectamente:

emanuel@emanuel-desktop:~$ sudo apt-get update
Des:1 [http://ar.archive.ubuntu.com](http://ar.archive.ubuntu.com) feisty Release.gpg [191B]
Obj [http://ar.archive.ubuntu.com](http://ar.archive.ubuntu.com) feisty/main Translation-es             
Obj [http://ar.archive.ubuntu.com](http://ar.archive.ubuntu.com) feisty/restricted Translation-es
Obj [http://ar.archive.ubuntu.com](http://ar.archive.ubuntu.com) feisty/universe Translation-es
Obj [http://ar.archive.ubuntu.com](http://ar.archive.ubuntu.com) feisty/multiverse Translation-es
Des:2 [http://ar.archive.ubuntu.com](http://ar.archive.ubuntu.com) feisty-updates Release.gpg [191B]
Des:3 [http://ubuntu.beryl-project.org](http://ubuntu.beryl-project.org) feisty Release.gpg [191B]         
Ign [http://ar.archive.ubuntu.com](http://ar.archive.ubuntu.com) feisty-updates/main Translation-es
Ign [http://ar.archive.ubuntu.com](http://ar.archive.ubuntu.com) feisty-updates/restricted Translation-es
Des:4 [http://ar.archive.ubuntu.com](http://ar.archive.ubuntu.com) feisty-security Release.gpg [191B]
Ign [http://ubuntu.beryl-project.org](http://ubuntu.beryl-project.org) feisty/main Translation-es
Des:5 [http://ubuntu.beryl-project.org](http://ubuntu.beryl-project.org) feisty Release [2965B]
Ign [http://ar.archive.ubuntu.com](http://ar.archive.ubuntu.com) feisty-security/main Translation-es
Obj [http://ubuntu.beryl-project.org](http://ubuntu.beryl-project.org) feisty/main Packages
Obj [http://ubuntu.beryl-project.org](http://ubuntu.beryl-project.org) feisty/main Sources
Ign [http://ar.archive.ubuntu.com](http://ar.archive.ubuntu.com) feisty-security/restricted Translation-es
Ign [http://ar.archive.ubuntu.com](http://ar.archive.ubuntu.com) feisty-security/universe Translation-es
Ign [http://ar.archive.ubuntu.com](http://ar.archive.ubuntu.com) feisty-security/multiverse Translation-es
Obj [http://ar.archive.ubuntu.com](http://ar.archive.ubuntu.com) feisty Release
Obj [http://ar.archive.ubuntu.com](http://ar.archive.ubuntu.com) feisty-updates Release
Obj [http://ar.archive.ubuntu.com](http://ar.archive.ubuntu.com) feisty-security Release
Obj [http://ar.archive.ubuntu.com](http://ar.archive.ubuntu.com) feisty/main Packages
Obj [http://ar.archive.ubuntu.com](http://ar.archive.ubuntu.com) feisty/restricted Packages
Obj [http://ar.archive.ubuntu.com](http://ar.archive.ubuntu.com) feisty/main Sources
Obj [http://ar.archive.ubuntu.com](http://ar.archive.ubuntu.com) feisty/restricted Sources
Obj [http://ar.archive.ubuntu.com](http://ar.archive.ubuntu.com) feisty/universe Packages
Obj [http://ar.archive.ubuntu.com](http://ar.archive.ubuntu.com) feisty/universe Sources
Obj [http://ar.archive.ubuntu.com](http://ar.archive.ubuntu.com) feisty/multiverse Packages
Obj [http://ar.archive.ubuntu.com](http://ar.archive.ubuntu.com) feisty/multiverse Sources
Obj [http://ar.archive.ubuntu.com](http://ar.archive.ubuntu.com) feisty-updates/main Packages
Obj [http://ar.archive.ubuntu.com](http://ar.archive.ubuntu.com) feisty-updates/restricted Packages
Obj [http://ar.archive.ubuntu.com](http://ar.archive.ubuntu.com) feisty-updates/main Sources
Obj [http://ar.archive.ubuntu.com](http://ar.archive.ubuntu.com) feisty-updates/restricted Sources
Obj [http://ar.archive.ubuntu.com](http://ar.archive.ubuntu.com) feisty-security/main Packages
Obj [http://ar.archive.ubuntu.com](http://ar.archive.ubuntu.com) feisty-security/restricted Packages
Obj [http://ar.archive.ubuntu.com](http://ar.archive.ubuntu.com) feisty-security/main Sources
Obj [http://ar.archive.ubuntu.com](http://ar.archive.ubuntu.com) feisty-security/restricted Sources
Obj [http://ar.archive.ubuntu.com](http://ar.archive.ubuntu.com) feisty-security/universe Packages
Obj [http://ar.archive.ubuntu.com](http://ar.archive.ubuntu.com) feisty-security/universe Sources
Obj [http://ar.archive.ubuntu.com](http://ar.archive.ubuntu.com) feisty-security/multiverse Packages
Obj [http://ar.archive.ubuntu.com](http://ar.archive.ubuntu.com) feisty-security/multiverse Sources
Descargados 2969B en 1s (1491B/s)
Leyendo lista de paquetes... Hecho

lo que no entiendo es que es eso de comentar y descomentar, te agradeceria si me explicaras un poco.

---

### Post by Al_maverick on 2007-07-01
en el archivo /etc/apt/sources.list, editalo con sudo, y ponele un # antes del nombre de cada repositorio.
para descomentarlo, borras el #

lo que hace eso, es que no tenga en cuenta esa linea, y entonces no toma los datos de ese repositorio.

---

### Post by Timbis on 2007-07-01
lo de update hace todo ok, gracias por la explicacion.
En el sinaptic cuando quiero instalar algo me da este error: 
[HTML]E: /var/cache/apt/archives/<Paquete.deb>: files list file for package `python-qt3' is missing final newline.
[/HTML]
Adrentro de la carpeta /var/cache/apt/archives/ hay un archivo llamado "Lock", y no se que, ya que no puedo abrirlo con nada. Tiene una crusesita arriba.

aca dejo mi sources.list, yo no veo ningun error (soy novato).

[HTML]# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://ar.archive.ubuntu.com/ubuntu/ feisty main restricted
deb-src http://ar.archive.ubuntu.com/ubuntu/ feisty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://ar.archive.ubuntu.com/ubuntu/ feisty-updates main restricted
deb-src http://ar.archive.ubuntu.com/ubuntu/ feisty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://ar.archive.ubuntu.com/ubuntu/ feisty universe
deb-src http://ar.archive.ubuntu.com/ubuntu/ feisty universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://ar.archive.ubuntu.com/ubuntu/ feisty multiverse
deb-src http://ar.archive.ubuntu.com/ubuntu/ feisty multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
 deb http://ar.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse
 deb-src http://ar.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse

deb http://ar.archive.ubuntu.com/ubuntu/ feisty-security main restricted
deb-src http://ar.archive.ubuntu.com/ubuntu/ feisty-security main restricted
deb http://ar.archive.ubuntu.com/ubuntu/ feisty-security universe
deb-src http://ar.archive.ubuntu.com/ubuntu/ feisty-security universe
deb http://ar.archive.ubuntu.com/ubuntu/ feisty-security multiverse
deb-src http://ar.archive.ubuntu.com/ubuntu/ feisty-security multiverse
deb http://ubuntu.beryl-project.org feisty main
deb-src http://ubuntu.beryl-project.org feisty main

[/HTML]

---

### Post by Al_maverick on 2007-07-02
Bueno, entonces hace lo siguiente:
edita el archivo con sudo: 
```
sudo kate /etc/apt/sources.list 
```
o 
```
sudo gedit /etc/apt/sources.list
```

en el archivo, pone un # delante de cada linea.
guarda el archivo y cerralo.

despues pone:
```
sudo apt-get update
sudo apt-get clean
sudo apt-get -f install

```

volve a abrir el archivo y saca los # de los nombres de los repositorios
guardalo y cerralo

pone de vuelta
```
sudo apt-get update
sudo apt-get -f install

```

Si te llega a tirar un error, adjuntalo y adjunta el archivo sources.list.

Lo que estas haciendo es resetear el cache de los repositorios, para ver si eso logra eliminar el problema con el archivo que bajo mal. Tene en cuenta que todos los pasos y el orden de los pasos son importantes, a pesar de que parezcan repetidos.

---

### Post by Timbis on 2007-07-02
nop, ya lo habia echo, lo volvi a hacer y (como simpre no dio ningun error), el problema sigue igual.
mi sources.list esta em mi port anterior.

---

### Post by Al_maverick on 2007-07-02
ok, vamos a ponernos un poco mas "salvajes", por asi decirlo.

Proba a hacer lo siguiente:
```
# sudo mv /var/lib/dpkg/info/ /var/lib/dpkg/info_moved

# sudo mkdir /var/lib/dpkg/info

<instala un paquete cualquiera>

# sudo mv /var/lib/dpkg/info/* /var/lib/dpkg/info_moved

# sudo rm /var/lib/dpkg/info

# sudo mv /var/lib/dpkg/info_moved /var/lib/dpkg/info
```

---

### Post by Timbis on 2007-07-02
SI!!! Luego de una semana de pelear con el demoniaco apt-get, Al_maverik encontro la solucion a mi problema!!. :D:D:D:D

estaria gueno si pudieras explicar que hicimos, que es lo que movimos? 
un abrazo de un Ubuntero.

---

### Post by Al_maverick on 2007-07-02
esto lo saque de un post de gente con problemas similares. habia muchos con el mismo problema, pero solo uno propuso esta solucion loca.
Por lo que entiendo, el sistema de apt se compone de dos componentes. apt maneja el update de los repositorios y bajar los archivos. dpkg maneja la instalacion en si.
que alguien me corrija, pero lo que movimos fue la informacion de los archivos instalados y el estado de dpkg, que tenia problemas.

y me alegro haber podido ayudar.

---

### Post by guillermolisi on 2007-07-02
O sea que en realidad habia cierta inconsistencia entre una estructura de archivos (dpkg) y la otra (apt), por eso los errores. 

Al renombrar [FONT=monospace]/var/lib/dpkg/info/, instalar un paquete (que se supone finaliza correctamente bien, sin errores, y que vuelve a crear la estructura para dpkg, la cosa se normaliza volviendo la relacion de los mismos consistente.[/FONT]

Entendieron algo parecido o me fui a los caños ?

---

