---
title: "Error: No se ha podido inicializar la información de los paquetes. Ayuda!"
date: 2012-10-01
forum: Asus Ubuntu Support (CLOSED)
---

### Post by Heomar on 2012-10-01
Hola! :)
Soy nueva usando ubuntu (12.04) y me ha mostrado el siguiente error:

No se ha podido inicializar la información de los paquetes.
'E:No se pudo tratar el archivo de paquetes /var/lib/apt/lists/ve.archive.ubuntu.com_ubuntu_dists_precise_universe_binary-i386_Packages (1), E:No se pudieron analizar o abrir las listas de paquetes o el archivo de estado.'

Por favor, ayúdenme! Gracias.

---

### Post by sigmatht on 2012-10-01
Start with checking your software sources.  

Ubuntu Software Center -- Edit -- Software Sources

---

### Post by Heomar on 2012-10-02
Verás, al abrir el centro de software de ubuntu automáticamente se cierra y me muestra otro error; Al abrir los detalles del error...

Dice: No se ha podido determinar el nombre del paquete binario o fuente.

Agradezco tu ayuda!

---

### Post by sigmatht on 2012-10-02
Try updating your source list manually.  

Open a terminal:  Control + Alt + T

Backup current sources.list:
sudo mv /etc/apt/sources.list /etc/apt/sources.list-broken


 Creates an empty sources.list to copy and paste new content.

Use gedit/nano whatever you choose and put in the standard source list:
sudo gedit /etc/apt/sources.list

Use the following link to get the default source list and paste it into your text editor.. 
[http://paste.ubuntu.com/1104980/](http://paste.ubuntu.com/1104980/)

Save the file. Close text editor.

sudo apt-get update
sudo apt-get upgrade

Paste any error messages you get into here.

---

### Post by Heomar on 2012-10-03
No tengo Backup instalado y, al intentar descargarlo me muestra el mismo error:

Leyendo lista de paquetes... ¡Error!
E: No se pudo tratar el archivo de paquetes /var/lib/apt/lists/ve.archive.ubuntu.com_ubuntu_dists_precise_universe_binary-i386_Packages (1)
E: No se pudieron analizar o abrir las listas de paquetes o el archivo de estado.

Ya esto es molesto :/ Gracias nuevamente por la ayuda!

---

### Post by sigmatht on 2012-10-03
go to terminal (control + alt + t):

 sudo gedit /etc/apt/sources.list

Copy everything in the file (control + a), paste it into: [http://paste.ubuntu.com/](http://paste.ubuntu.com/)

Then give us the link to it.

---

### Post by Heomar on 2012-10-04
Coloqué "sudo gedit /etc/apt/sources.list" y luego la password de root y me dice que la orden no fue encontrada :'(

Por favor, ayuda!

---

### Post by sigmatht on 2012-10-04
No comprendo.  No hablo mucho espanol... es possible para hablas en ingles?


**copiar y pegar los mensajes de error exactos que ****usted ve**

copiar:
control + shift + c 

You're not giving me much to work with here.  The command could not be found?  Which command.. I want to see what you type into terminal and the exact output it gives you.  

As far as I'm aware, if the command isn't found---then it would not ask for your password.  

try:
sudo apt-get install gedit

---

### Post by Heomar on 2012-10-05
heomar@heomar-O-E-M:~$ sudo apt-get install gedit 
[sudo] password for heomar: 
Leyendo lista de paquetes... ¡Error!
E: No se pudo tratar el archivo de paquetes /var/lib/apt/lists/ve.archive.ubuntu.com_ubuntu_dists_precise_universe_binary-i386_Packages (1)
E: No se pudieron analizar o abrir las listas de paquetes o el archivo de estado.
heomar@heomar-O-E-M:~$ 

Eso es lo que me muestra ;)

---

### Post by sigmatht on 2012-10-05
Bueno, tu sources.list es incorrecta. El uso de algún tipo de editor de texto, es necesario abrir el archivo / etc / apt / source.list y poner en los contenidos propios (I ligado a él por encima)

Usted debe tener gedit ya está instalado en su ordenador.

---

### Post by Heomar on 2012-10-06
No entiendo mucho tu español! :/ Te entendía más el inglés. 

El uso de algún tipo de editor de texto, es necesario abrir el archivo / etc / apt / source.list y poner en los contenidos propios (I ligado a él por encima)

No lo encuentro coherente :( 
Ten en cuenta que soy novata en ubuntu ;)
Ah! Ten mi correo [email]heomarf@gmail.com[/email] creo que sería mejor por ahí!

Gracias.

---

### Post by Heomar on 2012-10-08
Gracias!

---

