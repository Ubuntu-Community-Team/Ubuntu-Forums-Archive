---
title: "Problemas al actualizar Ubuntu con mi Modem Huawei MT810 de TELECOM"
date: 2007-03-24
forum: Argentina Team
---

### Post by angelcab on 2007-03-24
Bueno despues de muchos problemas pude hacer andar el modem HUAWEI de telecom Argentina en Ubuntu siguiendo esta guia: [http://69.60.114.106/www.kubuntu-es.org/public_html/?q=node/1470](http://69.60.114.106/www.kubuntu-es.org/public_html/?q=node/1470) 

al actualizar el equipo en el arranque ahora me da las opciones de la version instalada o la version actualizada ... cuando quiero entrar a la version actualizada el modem no me funciona ... o sea queda una sola luz prendida (la de power) ... trato de reinstalarlo siguiendo la misma guia pero no me deja... ya en el primer paso de instalar los linux headers me tira este error :

> 
matanga@matanga-desktop:~$ uname -r 
2.6.15-28-386
matanga@matanga-desktop:~$ sudo apt-get install build-essential linux-headers-2.6.15-28-386
Password:
Reading package lists... Done
Building dependency tree... Done
build-essential is already the newest version.
The following extra packages will be installed:
  linux-headers-2.6.15-28
The following NEW packages will be installed:
  linux-headers-2.6.15-28 linux-headers-2.6.15-28-386
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 7762kB of archives.
After unpacking 79.6MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Err [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main linux-headers-2.6.15-28 2.6.15-28.51
  Temporary failure resolving 'security.ubuntu.com'
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-security/main linux-headers-2.6.15-28 2.6.15-28.51
  Temporary failure resolving 'archive.ubuntu.com'
Err [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main linux-headers-2.6.15-28-386 2.6.15-28.51
  Temporary failure resolving 'security.ubuntu.com'
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-security/main linux-headers-2.6.15-28-386 2.6.15-28.51
  Temporary failure resolving 'archive.ubuntu.com'
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/l/linux-source-2.6.15/linux-headers-2.6.15-28_2.6.15-28.51_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/l/linux-source-2.6.15/linux-headers-2.6.15-28_2.6.15-28.51_i386.deb)  Temporary failure resolving 'archive.ubuntu.com'
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/l/linux-source-2.6.15/linux-headers-2.6.15-28-386_2.6.15-28.51_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/l/linux-source-2.6.15/linux-headers-2.6.15-28-386_2.6.15-28.51_i386.deb)  Temporary failure resolving 'archive.ubuntu.com'
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
matanga@matanga-desktop:~$

Alguien que me de una mano!!

---

### Post by Darth Trix on 2007-03-24
Tiralo a la mierda el Huawei y pedi que te manden un Ethernet.

---

### Post by angelcab on 2007-03-24
> **Darth Trix said:**
> Tiralo a la mierda el Huawei y pedi que te manden un Ethernet.


Gracias pero no te lo mandan te lo venden ..

---

### Post by Darth Trix on 2007-03-25
Si lloras mucho te lo mandan gratis, a mi lo dieron sin costo alguno.
Igualmente si tenes el Huawei en garantia tenes que pagar solo sesenta pesos.

---

### Post by mmilicich on 2007-04-02
angelcab:
Te cuento que yo tuve EXACTAMENTE EL MISMO PROBLEMA QUE VOS:
Ubuntu DApper, conexion a Internet por Arnet, Un modem USB-Adsl Huawei mt810
Me andaba el modem, y con las actualizaciones automaticas se me actualizo el kernel a la version 2.6.15-28-386... a partir de ahi dejò de andar el modem...

Te cuento COMO LO SOLUCIONE:

bootea el Ubuntu desde la version actualizada (la 2.6.15-28-386)

Verifica desde algun administrador de paquetes (x ej Synaptic) q sigas teniendo instalado el paquete build-essential (deberias tenerlo instalado, pues la actualizacion no lo desinstala, bah, a mi me lo dejo....)

Y lo q vas a necesitar es la instalacion de los paquetes:
br2684ctl.deb (ese ya lo tenias cuando configuraste todo para la version anterior, pero hay q instalarlo de nuevo)
y el MAS IMPORTANTE:
**[SIZE="3"]linux-headers-2.6.15-28[/SIZE]**
Como te decia, al no tener internet, no te va a servir hacer un:
sudo apt-get install linux-headers-2.6.15-28-386

Lo q tenes q hacer es (desde otro lugar en donde tengas Internet) bajarte los siguientes paquetes:
1) 
**linux-headers-2.6.15-28**
Lo bajas de [http://packages.ubuntu.com/dapper/devel/linux-headers-2.6.15-28](http://packages.ubuntu.com/dapper/devel/linux-headers-2.6.15-28)
(anda a la tablita donde dice "downloads" en esa pagina, y elegi la opcion "i386")
Luego te lleva a otra pagina con un unico link: ese es el paquete (son aprox 6Mb)
2) 
**linux-headers-2.6.15-28-386**
Lo bajas de [http://packages.ubuntu.com/dapper/devel/linux-headers-2.6.15-28-386](http://packages.ubuntu.com/dapper/devel/linux-headers-2.6.15-28-386)
(anda a la tablita donde dice "downloads" en esa pagina, y elegi la opcion "i386", es la unica opcion =))
Luego te lleva a otra pagina con un unico link: ese es el paquete (son aprox 834Kb)

Una vez q tenes los 2 paquetes, booteas el Ubuntu (la version actualizada: 2.6.15-28-386 !!)
E instalas ambos paquetes EN ESE ORDEN !!! (yo al principio los queria instalar sin querer en orden diferente...me volvi loco para darme cuenta q tenia q ser al reves)

Como instalarlos ? es facil !! hace doble click sobre el archivo: te abre el gestor de paquetes y le pedis q lo instale...listo  (te advierte q "en un canal existe la misma version y  q mejor lo instales desde un canal"...pero obviamente no podes instalarlo desde un canal sino tenes internet !! =)

LISTO !!
Ahora, si, segui el tutorial como estabas siguiendo !!
pero obviamente saltando el primer paso 
$ sudo apt-get install build-essential linux-headers-”uname -r”
Que es el q te estaba dando el error

Cualquier cosa avisame...
soy nuevo en esto de linux tambien...pero a lo mejor te puedo seguir ayudando...

Ah  !! Algo importante: al final, cuando estaba terminando el paso a paso, llegue a la parte q dice:
[COLOR="RoyalBlue"]"Esta es la parte más sencilla, solo tienen que hacer:
$ sudo pppd call adsl
Ingresan el password de usuario de kubuntu y les aparecerá esto:
Plugin rp-pppoe.so loaded.
Abran el navegador y voila!, a disfrutar de internet!."[/COLOR]
Le ponia sudo pppd call adsl, y nada !!! la lucecita de data no se prendia, y abria el firefox para navegar y no podia....
Lo q hice fue (desde la terminal):
$ sudo pppoe-start
Ahi despues de un ratito (15-20 seg) me aparecio
...................... CONNECTED !
Y entonces, si le puse de nuevo
$ sudo pppd call adsl

Y ahi levanto Internet!

Saludos
MA_Xx

PS: Me costo un HUEVO encontrar la data necesaria para lograrlo !!! Esto del Linux es a veces demasiado complicado !! =)

---

### Post by angelcab on 2007-04-02
> **mmilicich said:**
> 
PS: Me costo un HUEVO encontrar la data necesaria para lograrlo !!! Esto del Linux es a veces demasiado complicado !! =)

lo acabo de hacer funcionar !! mira entre desde el q no tenia actualizado y le di 

 sudo apt-get install build-essential linux-headers-2.6.15-28-adm64-generic


me los bajo y entre desde el que tenia el 2.6.15-28-amd64-generic y segui con la instalacion normal y listo ya estoy disfrutando !! 

muy bueno esto de renegar con linux porque vas aprendiendo cada vez mas !! 

Gracias totales 

ahora vamos por el beryl !!

---

### Post by Tongax on 2007-09-05
Gente, como va? Che, mi problema es que estoy tratando de instalar el Huawei USB de Telecom con Fiesty Fawn 7.04 (Kernel 2.6.20-15-generic), y siguendo este Howto ([http://www.ubuntu-es.org/index.php?q=node/45097](http://www.ubuntu-es.org/index.php?q=node/45097)), el moden linkea, pero al tirar el pppoe-start, me aparecen los puntos, pero despues de unos segundos (10-15 +o-), me tira TIME OUT!

Los datos con los cuales yo configuro la conexion son estos:

DNS: 200.42.0.110/200.42.97.110
VPI: 0
VCI: 33

Yo estoy en Zona Telecom, con la conexion de Flash.

Alguien me puede ayudar o me puede corregir en que estoy haciendo mal POR FAVOR!!!!

Saludos, TongaX

---

