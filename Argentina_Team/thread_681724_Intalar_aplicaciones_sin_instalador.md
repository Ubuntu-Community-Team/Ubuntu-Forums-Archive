---
title: "Intalar aplicaciones sin instalador"
date: 2008-01-29
forum: Argentina Team
---

### Post by h9005 on 2008-01-29
Tengo descargados en mi máquina estas aplicaciones: LiVES-0.9.8.7.tar.gz, LiVES-0.9.8.7.tar.bz2, diva-0.0.2.tar.gz, cuando hago doble clic abre el archivador pero no se como hacer para instalarlas. Y no entiendo bien las instucciones que traen. Como hago?

---

### Post by Mauro22 on 2008-01-29
Lo mas generico es 

Clic derecho, dale extraer aqui.

Despues con la consola te metes en la carpeta que se creo.

Y haces

./configure
sudo make
sudo make install


Sino, postea algun readme o leame para ver como se instala o la direccion para bajarlo asi lo veo mejor!

:lolflag:

---

### Post by h9005 on 2008-01-29
¿Como hago para meterme en la consola en esa carpeta? Está en mi home.
Y después escribo esas tres cosas por separado en la consola?

---

### Post by euzkoarima on 2008-01-29
> **h9005 said:**
> ¿Como hago para meterme en la consola en esa carpeta? Está en mi home.
Y después escribo esas tres cosas por separado en la consola?

en la terminal pones:
cd /path-a-esa-carpeta

Si por ejemplo la carpeta se llama LaCarpeta y la pusiste en tu escritorio (y tu usuario es YO) quedaría como

cd /home/YO/Escritorio/LaCarpeta

y si, después ingresas los otros comandos.

Saludos,

---

### Post by leo_rockway on 2008-01-29
> **Mauro22 said:**
> 
./configure
sudo make
sudo make install


Queria aclarar que no es necesario usar sudo para make.

---

### Post by sajnox on 2008-01-29
En mi opinion la mejor forma de instalar esos paquetes es con el comando alien, basicamente por que de esa manera es como si fuera un.deb y es lo hace mas facil para desinstalarlo

para usar alien

sudo alien -iv "archivo tar.gz"

Saludos

---

### Post by Mauro22 on 2008-01-29
> **leo_rockway said:**
> Queria aclarar que no es necesario usar sudo para make.

Gracias! Me confundi con el make install.

./configure
make
sudo make install

---

### Post by nemodot on 2008-01-29
Quisiera explicar que es lo que tenes entre las manos para entender como se instalan algunos programas en linux.

Esos archivos que quieres instalar son nada mas y nada menos que el código fuente del programa, con los comandos ./configure, make, y make install lo que haces es configurar para chequear que todo lo que necesita esta instalado y luego con make y make install se compila el programa, es decir, se traduce el código humano en el código de la computadora y se instala.

Es la forma más dificultosa de instalar en linux pero es la mejor. Yo siempre trato de evitar compilar un programa y busco el programa previamente compilado para instalar como un ejecutable de windows. En ubuntu son los .deb; también puedes instalar programas desde el synaptic o buscar por internet algun .deb del software que necesites.

Un buen sitio para encontrar .deb's es:

[http://www.getdeb.net/]("http://www.getdeb.net/")

Encontré el programa que buscabas ahi; [http://www.getdeb.net/app/LiVES](http://www.getdeb.net/app/LiVES)

Escoge tu versión y si tu sistema es de 32 o 64 bits y baja el .deb

Luego haz doble click y lo instalas.

---

### Post by User21 on 2008-01-30
[COLOR=black]COMO INSTALAR CUALQUIER COSA EN UBUNTU, segun ubuntu-ar! 
[/COLOR][http://ubuntu-ar.org/soporte/comos/instalar](http://ubuntu-ar.org/soporte/comos/instalar)

---

### Post by spg76 on 2008-01-30
> **User21 said:**
> [COLOR=black]COMO INSTALAR CUALQUIER COSA EN UBUNTU, segun ubuntu-ar! 
[/COLOR][http://ubuntu-ar.org/soporte/comos/instalar](http://ubuntu-ar.org/soporte/comos/instalar)

Ese artículo está un poco desactualizado.
En la Guia Ubuntu hay uno mucho mejor en [http://www.guia-ubuntu.org/index.php?title=A%C3%B1adir_aplicaciones](http://www.guia-ubuntu.org/index.php?title=A%C3%B1adir_aplicaciones)

---

### Post by h9005 on 2008-01-30
Gracias chicos la verdad se pasaron. Igual sigue sin quedarme claro cual es la mejor forma de instalar, más alla de que sea complicada. Con la consola o buscando un .deb. Gracias.

---

### Post by leo_rockway on 2008-01-30
la forma mas comoda, rapida y segura de instalar programas en ubuntu es usar los repositorios.

synaptic, adept, apt-get, aptitude... cualquiera de esos programas te instalan directamente desde los repos.

---

### Post by h9005 on 2008-01-31
Acá les posteo las instrucciones: yo no pude instalarlo. Es un editor de video, el diva.
= Installation =

Please check the RELEASE notes and our website for complete build
instructions and documentation:

[http://www.diva-project.org/wiki/Installation](http://www.diva-project.org/wiki/Installation)

Diva is using SCons as the build system. You need to have it installed
to build this software. For those who would like to start quick &
dirty, type:

        `scons`

to build diva. You can now run it using the `bin/diva-uninstalled.sh`
script. If you'd like to install it system-wide type:

        `scons install PREFIX=/usr`

Please refer to the wiki docs if in trouble.

---

