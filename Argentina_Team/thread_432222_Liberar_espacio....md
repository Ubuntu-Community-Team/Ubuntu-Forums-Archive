---
title: "Liberar espacio..."
date: 2007-05-03
forum: Argentina Team
---

### Post by fetova on 2007-05-03
holaa!! :cry: :cry: 

Pido ayuda!! [-o< 

Estaba actualizando mi compu de dapper a edgy y se me acabo el espacio en disco en medio proceso. No puedo usar el sudo aptitude clean debido a que esta bloqueado y no se libera a menos que termine de instalar,y ya borre todos mis archivos, no se que hacer :'( y por quedarse a medio proceso no jala el x-server :cry:  que puedo hacer?

Gracias de antemano :)

---

### Post by Gideon26 on 2007-05-03
hola primero que todo necesitamos saber el tamaño de tu disco y si tenes particiones, en el caso de tener particiones consejo mueve las particiones dando asi mas espacio a la particion de ubuntu edgy. el ultimo recurso seria formatear con el live de edgy y volver a instalar. saludos.

---

### Post by Al_maverick on 2007-05-03
Antes que volver a instalar, si lo de las particiones no surte efecto, o te pide reiniciar, yo haria lo siguiente:

- pkill apt-get
- sudo apt-get autoclean
- sudo apt-get dist-upgrade -d

En ese punto te va a decir cuanto necesita de espacio para bajar y para instalar. Verifica cuanto espacio tenes. Si no te alcanza, entonces fijate q podes borrar.

Si tenes q reiniciar y el x no te levanta, bootea a consola y segui las mismas instrucciones. COPIALAS ANTES DE REINICIAR ;)

una buena para tener en cuenta es: sudo dpkg-reconfigure xserver-xorg
Esa es por si el servidor de X no levanta, para reconfigurarlo desde la consola.

Suerte!!! Y cualquier cosa estamos por aca para seguir ayudando

---

### Post by fetova on 2007-05-04
> **Al_maverick said:**
> Antes que volver a instalar, si lo de las particiones no surte efecto, o te pide reiniciar, yo haria lo siguiente:

- pkill apt-get
- sudo apt-get autoclean
- sudo apt-get dist-upgrade -d

ya lo hice y ya esta continuando la instalacion :) No tengo consola. pero ya estoy acostombrandome... :rolleyes: 


> **Al_maverick said:**
> 
Suerte!!! Y cualquier cosa estamos por aca para seguir ayudando

Gracias!!!!! :) y si continuo con problemas tomare la palabra!

---

### Post by fetova on 2007-05-04
bueno... pues resulta que tuve otro problema :( ya  no prende!!! parece que no se instalo correctamente el paquete linux-headers y linux modules...algo

Ayuda!!!!!! :cry:

(el espacio ya no es problema :) jajajajajaajja :cry:)

---

### Post by Al_maverick on 2007-05-04
que queres decir exactamente con que no prende?

te aparece el menu de grub?
tenes opcion de volver al kernel anterior?

desde el live cd o del alternate de edgy podrias tratar de correr la reparacion, pero depende de exactamente cual sea el problema.

---

### Post by fetova on 2007-05-07
ya sirve!!!!!!!!!!!!!!

como?

no lo entiendo muy bien... :confused: reinicie algunas veces peleandome con que eth0 no queria funcionar y despues milagrosamente ya quiso, termine de instalar el sistema y no queria funcionar el xserver, di un dpkg-reconfigure xserver-xorg y reinicie, despues vi mi adorado ubuntu en modo grafico :D 

ha y paquetes rotos... pero no tengo gran problema con el sistema... mas que el que no ve el contenido de una particion...

Gracias!!!!!!!

---

### Post by Al_maverick on 2007-05-07
para solucionar los paquetes rotos, corre:

sudo apt-get update
sudo apt-get install -f

y la particion que no ve, fijate si la podes montar a mano con mount

---

### Post by fetova on 2007-05-08
> **Al_maverick said:**
> para solucionar los paquetes rotos, corre:

sudo apt-get update
sudo apt-get install -f

y la particion que no ve, fijate si la podes montar a mano con mount

la particion esta montada ya, solo se habia borrado la linea a la hora de la actualizacion en fstab, la agrege y ya esta... el problema que si hay es este:


```
federico@fetova:~$ sudo apt-get update
Des:1 http://archive.ubuntu.com edgy Release.gpg [191B]                
Des:2 http://archive.ubuntu.com edgy/universe Translation-es [144kB]
Des:3 http://security.ubuntu.com edgy-security Release.gpg [191B]
Ign http://security.ubuntu.com edgy-security/universe Translation-es
Ign http://security.ubuntu.com edgy-security/multiverse Translation-es
Ign http://security.ubuntu.com edgy-security/main Translation-es
Ign http://security.ubuntu.com edgy-security/restricted Translation-es
Ign http://security.ubuntu.com edgy-security/universe Translation-es
Ign http://security.ubuntu.com edgy-security/multiverse Translation-es
Obj http://security.ubuntu.com edgy-security Release         
Des:4 http://security.ubuntu.com edgy-security/universe Packages [40.4kB]
93% [4 Packages bzip2 0] [2 Translation-es 128914/144kB 89%] [Esperando las cabbzip2: (stdin) is not a bzip2 file.
Err http://security.ubuntu.com edgy-security/universe Packages                 
  El subproceso bzip2 devolvió un código de error (2)
Des:5 http://archive.ubuntu.com edgy/multiverse Translation-es [332B]          
Des:6 http://archive.ubuntu.com edgy/universe Translation-es [144kB]           
62% [2 Translation-es bzip2 0] [6 Translation-es 1241/144kB 0%] [Esperando las 
bzip2: Compressed file ends unexpectedly;
        perhaps it is corrupted?  *Possible* reason follows.
bzip2: Inappropriate ioctl for device
        Input file = (stdin), output file = (stdout)

It is possible that the compressed file(s) have become corrupted.
You can use the -tvv option to test integrity of such files.

You can use the `bzip2recover' program to attempt to recover
data from undamaged sections of corrupted files.

Ign http://archive.ubuntu.com edgy/universe Translation-es                     
Obj http://security.ubuntu.com edgy-security/multiverse Packages               
Obj http://security.ubuntu.com edgy-security/main Packages      
Obj http://security.ubuntu.com edgy-security/restricted Packages
Obj http://security.ubuntu.com edgy-security/main Sources       
Obj http://security.ubuntu.com edgy-security/restricted Sources 
Des:7 http://security.ubuntu.com edgy-security/universe Packages [40.4kB]
Obj http://security.ubuntu.com edgy-security/multiverse Packages 
Obj http://security.ubuntu.com edgy-security/universe Sources    
Obj http://security.ubuntu.com edgy-security/multiverse Sources  
57% [6 Translation-es 110141/144kB 76%]bzip2: (stdin) is not a bzip2 file.
Err http://security.ubuntu.com edgy-security/universe Packages
  El subproceso bzip2 devolvió un código de error (2)
Des:8 http://archive.ubuntu.com edgy/multiverse Translation-es [332B]
Des:9 http://archive.ubuntu.com edgy/main Translation-es [36.7kB]
Des:10 http://archive.ubuntu.com edgy/restricted Translation-es [14B]
Des:11 http://archive.ubuntu.com edgy-updates Release.gpg [191B] 
Ign http://archive.ubuntu.com edgy-updates/universe Translation-es
Ign http://archive.ubuntu.com edgy-updates/multiverse Translation-es
Ign http://archive.ubuntu.com edgy-updates/main Translation-es
Ign http://archive.ubuntu.com edgy-updates/restricted Translation-es
Ign http://archive.ubuntu.com edgy-updates/universe Translation-es
Ign http://archive.ubuntu.com edgy-updates/multiverse Translation-es
Obj http://archive.ubuntu.com edgy Release                  
Obj http://archive.ubuntu.com edgy-updates Release                           
Obj http://archive.ubuntu.com edgy/universe Packages                           
Obj http://archive.ubuntu.com edgy/multiverse Packages                         
Obj http://archive.ubuntu.com edgy/universe Packages         
Obj http://archive.ubuntu.com edgy/multiverse Packages       
Obj http://archive.ubuntu.com edgy/main Packages             
Obj http://archive.ubuntu.com edgy/restricted Packages       
Obj http://archive.ubuntu.com edgy/main Sources
Obj http://archive.ubuntu.com edgy/restricted Sources    
Obj http://archive.ubuntu.com edgy/universe Sources
Obj http://archive.ubuntu.com edgy/multiverse Sources
Obj http://archive.ubuntu.com edgy-updates/universe Packages
Obj http://archive.ubuntu.com edgy-updates/multiverse Packages
Obj http://archive.ubuntu.com edgy-updates/main Packages
Obj http://archive.ubuntu.com edgy-updates/restricted Packages
Obj http://archive.ubuntu.com edgy-updates/main Sources
Obj http://archive.ubuntu.com edgy-updates/restricted Sources
Obj http://archive.ubuntu.com edgy-updates/universe Packages
Obj http://archive.ubuntu.com edgy-updates/multiverse Packages
Obj http://archive.ubuntu.com edgy-updates/universe Sources
Obj http://archive.ubuntu.com edgy-updates/multiverse Sources
Descargados 326kB en 4s (70.4kB/s)
Imposible obtener http://security.ubuntu.com/ubuntu/dists/edgy-security/universe/binary-i386/Packages.bz2  El subproceso bzip2 devolvió un código de error (2)
Imposible obtener http://security.ubuntu.com/ubuntu/dists/edgy-security/universe/binary-i386/Packages.bz2  El subproceso bzip2 devolvió un código de error (2)
Leyendo listas de paquetes... Hecho
W: Duplicate sources.list entry http://archive.ubuntu.com edgy/universe Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_edgy_universe_binary-i386_Packages)
W: Duplicate sources.list entry http://archive.ubuntu.com edgy/universe Translation-es (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_edgy_universe_i18n_Translation-es)
W: Duplicate sources.list entry http://archive.ubuntu.com edgy/multiverse Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_edgy_multiverse_binary-i386_Packages)
W: Duplicate sources.list entry http://archive.ubuntu.com edgy/multiverse Translation-es (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_edgy_multiverse_i18n_Translation-es)
W: Duplicate sources.list entry http://security.ubuntu.com edgy-security/multiverse Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_edgy-security_multiverse_binary-i386_Packages)
W: Duplicate sources.list entry http://archive.ubuntu.com edgy-updates/universe Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_edgy-updates_universe_binary-i386_Packages)
W: Duplicate sources.list entry http://archive.ubuntu.com edgy-updates/multiverse Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_edgy-updates_multiverse_binary-i386_Packages)
W: Tal vez quiera ejecutar «apt-get update» para corregir estos problemas
E: Algunos archivos de índice no se han podido descargar, se han ignorado,
o se ha utilizado unos antiguos en su lugar.
federico@fetova:~$ sudo apt-get install -f
Leyendo listas de paquetes... Hecho
Creando árbol de dependencias       
Leyendo información de estado... Hecho
0 actualizados, 0 se instalarán, 0 para eliminar y 1 no actualizados.
federico@fetova:~$ 
```
luego puse...
```
federico@fetova:~$ sudo apt-get dist-upgrade
Leyendo listas de paquetes... Hecho
Creando árbol de dependencias       
Leyendo información de estado... Hecho
Calculando la actualización... Listo
Los siguientes paquetes se han retenido:
  python-htmlgen
0 actualizados, 0 se instalarán, 0 para eliminar y 1 no actualizados.
federico@fetova:~$ 
```
no entiendo bien :confused:

---

